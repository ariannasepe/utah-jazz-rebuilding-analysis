# Utah Jazz Rebuild Model

**A data-driven decision-support model for rebuilding the Utah Jazz roster**, built around the 2024-25 season. The project combines exploratory analysis, player profiling, a market acquisition model and a draft scouting model.

> The basketball statistics used in this project were obtained from [Basketball Reference](https://www.basketball-reference.com). The data is provided here only in limited form for demonstration purposes. For full datasets, please visit Basketball Reference directly.

## Overview

This repository is the analytical companion of my master's thesis, ***Data Science Applied to NBA Team Building: Rebuilding Strategies for the Utah Jazz***. The central question is simple: if a front office had to rebuild this roster, which decisions would the data support, and how far can they be trusted?

The work follows the same path a front office would take:

1. **Diagnosis (exploratory analysis).** Minutes, scoring, efficiency, shot charts and salaries for the 2024-25 roster, compared by position with playoff teams. The roster has a solid frontcourt but lacks a guard who combines playmaking and scoring, and its defensive production (steals, blocks) lags behind competitive teams.
2. **Player profiling.** Every player gets an automatic report: estimated offensive role, impact score and tier, K-Means archetype, comparable players and a radar chart.
3. **Decision model for the roster (thesis Chapter 3).** Five Python classes work in sequence:
   - `EnhancedPlayerRanker` scores players from their normalized box-score statistics.
   - `EnhancedTradeabilityRanker` estimates how tradeable each player is, based on age, salary and performance. Players in the future core are excluded.
   - `RosterNeedsAnalyzer` computes the needs of the roster that would remain after the trades, by position and by skill, plus the cap space left.
   - `AcquisitionTargetGenerator` turns those needs into ideal target profiles.
   - `PlayerMatcher` compares the targets with free agents and trade targets. It scores position, age, salary (with a hard cap on out-of-reach salaries), statistics and availability.
4. **Draft model (thesis Chapter 4).** The same logic is applied to the 2025 draft, with the four Jazz picks (5, 21, 43, 53). `DraftNeedsAnalyzer`, `ProspectScorer`, `BPARanker`, `PickConstraintFilter` and `DraftMatcher` simulate the board with a Best Player Available ranking and then rank the prospects realistically available at each pick by fit with the team's needs.

### Limits of the model

The model is meant to **support decisions, not replace them**, and its limits are stated explicitly:

- **Draft prospects.** Fit scores are not rescaled to NBA benchmarks. College and non-NCAA statistics are not directly comparable with NBA ones, so draft percentiles are computed within each competitive context (NCAA and non-NCAA) and should be read as relative to that group.
- **Salaries.** Salaries of free agents and of players without public contract data are estimated with a proxy based on performance, age and experience.
- **Tradeability.** A high tradeability score does not mean a player *should* be traded. It reflects contract and statistical factors, not a normative recommendation.

## Repository structure

```
utah-jazz-rebuilding-analysis/
├── docs/
│   ├── 02_analisi_IT.html
│   ├── 02_analysis_EN.html
│   └── index.html
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_analisi_IT.ipynb
│   └── 02_analysis_EN.ipynb
├── LICENSE
├── requirements.txt
└── README.md
```

### `01_data_cleaning.ipynb`

Loads the raw data sources, merges them, handles missing values, and exports the cleaned dataset (`utah_jazz_clean.csv`) used by the analysis notebook.

### `02_analysis_EN.ipynb` (and `02_analisi_IT.ipynb`)

The full analysis, in English and in Italian. Sections:

1. Setup and data loading
2. Roster analysis
3. Offensive and defensive contribution by role
4. Comparison with playoff teams
5. Offensive efficiency diagnosis
6. Points by role and shot charts
7. Salaries
8. Offensive/defensive weight and clustering
9. Player analysis (automatic reports per player)
10. Decision-support model v4 (Chapter 3)
11. NBA Draft 2025 (Chapter 4)

## Setup

```
pip install -r requirements.txt
```

Run the notebooks in order: `01_data_cleaning.ipynb` first to generate the cleaned dataset, then `02_analysis_EN.ipynb` (or the Italian version).

## Note on interactive charts

The notebooks use **Plotly** for visualizations. Since GitHub does not render JavaScript in notebook previews, charts may not display directly on github.com. To view them:

- Open the notebook locally (Jupyter/VS Code), or
- Open the exported HTML files in the `docs/` folder

## Author

**Arianna**
