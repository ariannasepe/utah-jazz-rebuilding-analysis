# Utah Jazz Rebuild Model

Analysis and modeling pipeline exploring the Utah Jazz rebuilding process, combining a draft fit system with a roster salary-performance fit model.

The basketball statistics used in this project were obtained from Basketball Reference. The data is provided here only in limited form for demonstration purposes.
For full datasets, please visit Basketball Reference directly.

## Overview

This project is part of a thesis chapter on team-building strategy in the NBA. It looks at two connected questions:

- **Draft fit**: which draft prospects best match the Jazz's rebuilding needs, using a percentile-based normalization approach across leagues (`DraftMatcher` pipeline)
- **Roster fit**: how current roster salary allocation compares to on-court performance, with Lauri Markkanen as a specific case study

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
└── README.md
```

### `01_data_cleaning.ipynb`
Loads the raw data sources, merges them, handles missing values, and exports the cleaned dataset (`utah_jazz_clean.csv`) used by the analysis notebook.

### `02_analysis_EN.ipynb`
Reads the cleaned dataset and runs the full analysis: draft fit scoring, roster salary-performance fit, and interactive Plotly visualizations.

## Setup

```bash
pip install -r requirements.txt
```

Run the notebooks in order: `01_data_cleaning.ipynb` first to generate the cleaned dataset, then `02_analysis.ipynb`.

## Note on interactive charts

This notebook uses Plotly for visualizations. Since GitHub does not render JavaScript in notebook previews, charts may not display directly on github.com. To view them:

- Open the notebook locally (Jupyter/VS Code), or
- Open the exported HTML files in the `docs/` folder
  
## Author

Arianna
