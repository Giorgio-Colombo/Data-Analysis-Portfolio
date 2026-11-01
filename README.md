# Data Analysis Portfolio

Applied data analysis projects in **Python, SQL and Tableau**, built on open and public datasets. Each project lives in its own folder with a short write-up of the question, data, method and findings.

> Looking for the econometrics work? See [**Econometrics_Portfolio**](https://github.com/Giorgio-Colombo/Econometrics_Portfolio).
> Labour-market analysis with Eurostat data: [**european-labor-market-analysis**](https://github.com/Giorgio-Colombo/european-labor-market-analysis).

## Projects

| Project | Question | Methods | Scale |
|---|---|---|---|
| [**Clash Royale 2026: meta analysis with a discrete-choice model**](clash-royale-2026-meta-econometrics/) | Which cards and decks are *actually* strong once card levels and single-player dominance are controlled for? | Sparse logistic regression, Wilson confidence intervals, 64-bit deck encoding, Spearman rank analysis | ~10M matches |
| [**Clash Royale 2021: upper-ladder deck analysis**](clash-royale-2021-battles/) | Which decks win most across trophy brackets? | Data cleaning, descriptive statistics, win-rate ranking by bracket | ~719k battles |
| [**Lichess chess games: SQL & EDA**](lichess-chess-sql/) | How large is the first-mover advantage, and how do ratings and openings shape outcomes? | SQLite, CTEs, conditional aggregation, pandas, seaborn | ~20k games |

Related work, kept in its own repositories:

| Project | Where |
|---|---|
| European unemployment and labour participation, 2016-2025 (Eurostat) | [european-labor-market-analysis](https://github.com/Giorgio-Colombo/european-labor-market-analysis) |
| Boston Housing: multiple linear regression and model selection (SPSS) | [Econometrics_Portfolio / boston-housing-regression](https://github.com/Giorgio-Colombo/Econometrics_Portfolio/tree/main/boston-housing-regression) |

## Tools

Python (pandas, NumPy, SciPy, scikit-learn, matplotlib, seaborn) · SQL (SQLite) · Tableau · Jupyter / Google Colab · Kaggle

Dashboards: [Tableau Public](https://public.tableau.com/app/profile/giorgio.colombo/vizzes) · Notebooks: [Kaggle](https://www.kaggle.com/giorgiocolomb0)

## Running the notebooks

Each notebook has an *Open in Colab* badge and downloads its dataset automatically (via `kagglehub`), so no local setup is needed.

> **Note:** some notebooks still contain Italian comments and chart labels. English versions are in progress.
