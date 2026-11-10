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
│   └── processed/            # Generated data; excluded from Git
├── results/
│   ├── tables/               # Validation scores, error bars, and row counts
│   └── figures/              # Figures produced by notebook code
├── reports/
│   ├── proposal.txt
│   └── baseline.txt
├── presentation/             # Slides and presentation material
├── docs/
│   └── protocol.json         # Prespecified cleaning, splits, and tuning settings
├── requirements.txt
└── .gitignore
```

Keep this layout for the rest of the project. Add the boosting comparison as `notebooks/02_boosting.ipynb` and final evaluation as `notebooks/03_final_evaluation.ipynb`. Save their tables and figures under `results/`, the paper under `reports/`, and slides under `presentation/`.

## Run the baseline

Tested with Python 3.12. From this project directory:

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
jupyter lab
```

On Windows, activate the environment with `.venv\Scripts\activate` instead.

Open `notebooks/01_baseline.ipynb` and run all cells in order. The notebook works with its kernel started in either the project root or `notebooks/`. It reads the five workbooks from `data/raw/`, creates the processed tables, fits ridge, computes validation error bars, runs a fixed-model paired-bootstrap diagnostic, and draws `results/figures/baseline.png` with Matplotlib. It does not generate the written reports.

The notebook is self-contained and does not require the older project scripts. Exact installed package versions are recorded in `requirements.txt`.

## Data and evaluation

The [NYC Department of Finance dataset](https://www.nyc.gov/site/finance/property/property-rolling-sales-data.page) contains 82,576 sales in the frozen October 2025–September 2026 snapshot. Categories 01–03 and a $10,000 minimum leave 18,672 observations. The price screen does not certify market-value transactions.

Three expanding training windows validate on January–February, March–April, and May–June 2026. July–September's 4,445 sales are reserved for the final evaluation. The baseline notebook audits parcel overlap but does not predict or score this test quarter.

Imputation, encoding, and scaling are fit only on each training window. Ridge selects alpha 10 from 12 penalties. Mean validation log-price MAE is approximately 0.26585, with a conditional 95% tax-block bootstrap interval of [0.25800, 0.27421]. These intervals exclude tuning uncertainty and future market shifts. The fixed XGBoost dry run is not the final tuned model comparison.

## Upload to GitHub

Create an empty repository on GitHub. From this directory, run:

```bash
git init
git add .
git commit -m "Add baseline notebook and frozen NYC sales data"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
git push -u origin main
```

Replace the remote URL with your own repository. Generated processed data are ignored by Git and can be recreated from the tracked raw workbooks. After uploading, replace the open code link in `reports/baseline.txt` with the notebook's GitHub URL.

## AI assistance

Codex assisted with implementation and editing. Group members should review the retained code, independently rerun the analysis, and verify numerical claims before submission.
