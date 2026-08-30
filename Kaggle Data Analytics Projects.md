# Kaggle Analytics Projects

This repository serves as a centralized portfolio and index for my data science, analytics, and econometric exploration projects hosted on [Kaggle](https://www.kaggle.com/). Each project includes exploratory data analysis (EDA), statistical modeling, and database querying applied to real-world datasets.

---

## Project Index

| # | Project Title | Primary Focus | Tech Stack | Kaggle Link |
|---|---------------|---------------|------------|-------------|
| 01 | [Lichess Chess Matches: SQL & EDA](#01---lichess-chess-matches-sql--exploratory-data-analysis) | Relational Database Analysis & Game Theory | SQLite, SQL, Python, Pandas | [View Notebook](https://www.kaggle.com/) |

---

## Project Details

### 01 - Lichess Chess Matches: SQL & Exploratory Data Analysis

* **Dataset:** [Lichess Games Dataset](https://www.kaggle.com/datasets/kforeman/keltonforeman-bta419-chess-set) (20,058 games)
* **Tech Stack:** SQLite, SQL (`ipython-sql`, CTEs, Conditional Aggregations), Python, Pandas, Matplotlib / Seaborn
* **Notebook Link:** [Kaggle Notebook]*(https://www.kaggle.com/code/giorgiocolomb0/lichessgamesanalysis)*

#### Overview
An end-to-end relational data analysis examining match outcomes, first-mover advantage, and opening effectiveness across 20,000+ online chess games from Lichess. The raw dataset was ingested into an embedded SQLite database to perform structured SQL queries and statistical aggregations directly inside a Jupyter/Kaggle environment.

#### Key Analytical Highlights
* **First-Mover Advantage:** Evaluated baseline White vs. Black win distributions and isolated the structural advantage of moving first in skill-controlled matches ($|\Delta \text{Elo}| \le 25$).
* **Game Termination Mechanisms:** Classified victory conditions (`mate`, `resign`, `outoftime`, `draw`) to analyze how games conclude across different pairings.
* **Rating Dynamics & Upsets:** Segmented players across official 7-tier Lichess rating bands (`<1200` Novice up to `2200+` Master) to observe win probability curves and upset frequencies.
* **Opening Repertoire Analysis:** Implemented multi-tier Common Table Expressions (CTEs) to evaluate win rates and draw tendencies for individual openings across different Elo brackets.

---

## Future Additions
*More projects will be documented here as new notebooks and analyses are published on Kaggle.*
