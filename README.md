# NYC home price prediction

How much does gradient boosting improve future sale-price predictions over a well-specified ridge model for NYC one- to three-family homes?

Course project by The Outliers: Kuangye, Tianlin, and Jiayi.

## Project structure

```text
nyc-home-price-prediction/
├── notebooks/
│   └── 01_baseline.ipynb
├── data/
│   ├── raw/                  # Frozen original borough workbooks and checksums
├── results/
│   ├── tables/               # Validation scores, error bars, and row counts
│   └── figures/              # Figures produced by notebook code
├── docs/
│   └── protocol.json         # Prespecified cleaning, splits, and tuning settings
├── requirements.txt
└── .gitignore
```


## Run the baseline

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
jupyter lab
```

Open `notebooks/01_baseline.ipynb` and run all cells in order. 

## Data and evaluation

The [NYC Department of Finance dataset](https://www.nyc.gov/site/finance/property/property-rolling-sales-data.page) contains 82,576 sales in the frozen October 2025–September 2026 snapshot. Categories 01–03 and a $10,000 minimum leave 18,672 observations.
