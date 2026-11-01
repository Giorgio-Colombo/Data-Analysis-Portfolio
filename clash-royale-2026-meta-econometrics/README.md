# Clash Royale 2026: meta analysis with a discrete-choice model

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Giorgio-Colombo/Data-Analysis-Portfolio/blob/main/clash-royale-2026-meta-econometrics/clash_royale_2026_meta_econometrics.ipynb)

## Question
Raw win rates in a competitive ladder are misleading. Which cards and decks are genuinely strong once we correct for two biases?

1. **Card-level bias ("pay-to-win"):** a deck can show a high win rate simply because its cards are, on average, upgraded to higher levels than the opponent's.
2. **Player concentration bias:** a deck can look dominant because a single elite player plays it thousands of times.

## Data
Public Kaggle dataset *Clash Royale matchups, June 2026* (`jackmangione/clash-royale-matchups-june2026`): **9,960,921 ladder matches** and **6,420,945 unique players** after filtering to ladder games.

## Method
- **Memory-efficient ingestion:** parquet filtering at read time, player IDs factorised to `int32`, duplicate removal on `(time, winner, loser)`.
- **Differential logistic regression:** each match is randomly assigned to side A/B to balance the outcome, with a sparse card-difference matrix plus a card-level difference term (`b_lvl`).
- **64-bit deck encoding:** every 8-card deck is sorted and packed into a single `uint64`, which makes grouping millions of decks fast.
- **Wilson 95% confidence intervals:** decks are ranked by how far their win rate exceeds the rate expected from levels alone, using a conservative lower bound.
- **Robustness filters:** at least 30 distinct players per deck and at most 10% of games from the top player.

## Key results
| Metric | Value |
|---|---|
| ROC-AUC, cards only | 0.650 |
| ROC-AUC, levels only | 0.665 |
| ROC-AUC, cards + levels | **0.711** |
| Level effect (logit coefficient per +1 average level, level-only model) | 0.844 |
| Average deck level, winners vs losers | 13.47 vs 13.25 |
| Rank correlation of card effects with vs without level control (171 cards) | 0.943 |
| Rank correlation of raw win rate vs level-adjusted effect | 0.749 |
| Distinct decks / decks with at least 300 games | 6,389,317 / 2,277 |

Reading these results: level carries slightly more predictive signal than card choice alone (AUC 0.665 vs 0.650), and the two together reach 0.711. Controlling for level changes the card ranking only modestly (Spearman 0.943). The lower 0.749 against raw win rates also reflects opponent mix and regularisation, so it should not be read as level bias alone.

## Limitations and open issues
- **The deck-level results are not credible yet.** The decks ranked as "robust" show win rates of 85-92% over hundreds of games and hundreds of distinct players, and several of the most-played decks show 10-21%. Matchmaking keeps win rates near 50%, so this points to how the dataset was collected (for example non-human opponents or a biased sample of matches) rather than to deck strength. The deck ranking must not be read as strategy advice until this is investigated.
- **The level coefficient comes from a level-only model**, so it also absorbs card effects. The combined model's coefficient would be cleaner.
- **Wilson intervals assume independent games**, but the same players repeat decks, player skill is unobserved, and 2,277 decks are ranked at once (multiple comparisons). Results are associations, not causal effects.

## Reproduce
Open the notebook in Colab (badge above). The dataset is downloaded automatically with `kagglehub`.

*Note: notebook comments and chart labels are currently in Italian.*
