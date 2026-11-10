# NYC home price prediction

How much does gradient boosting improve future sale-price predictions over ridge regression for NYC one- to three-family homes?

## Structure

```text
notebooks/01_baseline.ipynb   Data cleaning, ridge validation, bootstrap, and plotting
data/raw/                   Five original workbooks and source checksums
results/tables/             Validation scores, error bars, and row counts
results/figures/            Matplotlib figures
docs/protocol.json          Prespecified cleaning, splits, and tuning settings
requirements.txt            Python package versions
.gitignore                  Local files excluded from Git
```

## Run

Use Python 3.12. From the project root:

```bash
python -m pip install -r requirements.txt
jupyter lab notebooks/01_baseline.ipynb
```

Run the notebook cells in order. It reads `data/raw/`, keeps cleaned datasets in memory, and saves only result tables and figures. The kernel can start in the project root or `notebooks/`.

The frozen data cover October 2025–September 2026. July–September remains held out for final performance evaluation. See `data/raw/README.md` for the source and `docs/protocol.json` for the evaluation plan.
