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
| Level effect (logit coefficient per +1 average level) | 0.844 |
| Average deck level, winners vs losers | 13.47 vs 13.25 |
| Rank correlation of card effects with vs without level control (171 cards) | 0.943 |
| Rank correlation of raw win rate vs level-adjusted effect | 0.749 |
| Distinct decks / decks with at least 300 games | 6,389,317 / 2,277 |

Takeaway: card level carries as much predictive signal as card choice, so rankings based on raw win rate are noticeably distorted. Adjusting for level changes which cards look strong.

## Reproduce
Open the notebook in Colab (badge above). The dataset is downloaded automatically with `kagglehub`.

*Note: notebook comments and chart labels are currently in Italian.*
