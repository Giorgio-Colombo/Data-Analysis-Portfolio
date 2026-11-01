# Clash Royale 2021: upper-ladder deck analysis

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Giorgio-Colombo/Data-Analysis-Portfolio/blob/main/clash-royale-2021-battles/clash_royale_2021_battles.ipynb)

## Question
Which decks and cards accumulate the most wins in the upper ladder, and does that change across trophy brackets?

## Data
Kaggle dataset *Clash Royale battles, upper ladder, December 2021* (`nonrice/clash-royale-battles-upper-ladder-december-2021`): **718,886 battles**, 20 variables. Quality checks found no missing values, card IDs within the expected range, and a binary outcome.

## What the notebook does
- Cleaning and consistency checks
- Variable classification and descriptive statistics
- Deck identification, order-invariant, via sorted card IDs: **1,437,772 decks played, 327,658 unique**
- Top 10 decks by **total number of wins** (these are mostly the most-played decks, with win rates between 48.7% and 55.3%)
- Top 5 decks per trophy bracket (below 6,300 / 6,300-6,600 / 6,600-7,000 / above), then a cross-bracket comparison
- Card with the most wins overall: **Fireball**, 226,342 wins in 452,233 appearances (50.05% win rate)

## Interpretation
Rankings by total wins measure **popularity** as much as strength: a deck played twice as often collects twice the wins. With matchmaking keeping win rates near 50%, differences in win rate between top decks are small and no confidence intervals are reported. Read the results as a description of the meta, not as evidence that a deck is stronger.

*Note: notebook comments and chart labels are currently in Italian.*
