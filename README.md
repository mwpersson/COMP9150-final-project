# COMP9150 Project 2 — Cybersecurity Data Exploration and Modeling

This project contains exploratory data analysis (EDA), anomaly detection, and attack classification experiments across multiple cybersecurity datasets using Python notebooks.

## Project Scope

The notebooks cover:

- **EDA and preprocessing**
- **Label construction** (for LANL Cyber1 using `redteam.txt`)
- **Dimensionality reduction** (PCA, t-SNE, UMAP)
- **Clustering** (KMeans, DBSCAN, Agglomerative)
- **Anomaly detection** (Isolation Forest, LOF, LSTM Autoencoder, ensembles)
- **Supervised attack classification** (Random Forest, Decision Tree, XGBoost, LSTM)

## Datasets Used

- **CIC-IDS2017** (`cic-ids2017-eda.ipynb`)
- **LANL Cyber1** (`cyber1.ipynb`, `cyber1-eda.ipynb`, `cyber1-sampled.ipynb`)
- **LANL Auth dataset variant** (`lanl-auth-eda.ipynb`)
- **UNSW-NB15** (`UNSW-NB15-EDA.ipynb`)

> Some notebooks assume local files under `./data/...`, while others can run in Colab (Drive path supported in `cyber1-eda.ipynb`).

## Repository Layout

- `README.md` — project documentation
- `cic-ids2017-eda.ipynb` — EDA for CIC-IDS2017 traffic labels
- `cyber1.ipynb` — Cyber1 labeling + sampling pipeline
- `cyber1-eda.ipynb` — Cyber1 large-scale EDA and anomaly workflow
- `cyber1-tests.ipynb` — EDA and anomaly models on sampled labeled Cyber1 data
- `lanl-auth-eda.ipynb` — LANL auth dataset analysis, visualization, clustering, anomaly checks
- `UNSW-NB15-tests.ipynb` — UNSW-NB15 EDA + multiclass attack modeling

## Environment Setup (macOS / VS Code)

1. Create and activate a virtual environment:

   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

2. Install core dependencies:

   ```bash
   pip install --upgrade pip
   pip install pandas numpy polars seaborn matplotlib scikit-learn scipy umap-learn imbalanced-learn xgboost tensorflow pyarrow kagglehub
   ```

3. In VS Code:
   - Open this folder.
   - Select the `.venv` Python interpreter.
   - Run notebooks cell-by-cell.

## Data Setup

Place datasets under a structure like:

- `data/cic-ids-2017/...`
- `data/cyber1/auth.txt`
- `data/cyber1/redteam.txt`
- `data/lanl-auth/...`

For UNSW-NB15, the notebook can download data via `kagglehub`.

LANL cyber1 dataset available [here](https://csr.lanl.gov/data/cyber1/)

LANL auth dataset available [here](https://csr.lanl.gov/data/auth/)

CIC-IDS2017 dataset available [here](https://cicresearch.ca/CICDataset/CIC-IDS-2017/)

## Typical Workflow

1. Run **EDA notebook** for the dataset.
2. For Cyber1:
   - Run `cyber1.ipynb` to create labels and sampled output.
   - Output file: `./data/cyber1/labeled_sample.csv`
3. Run downstream modeling notebooks (e.g., `cyber1-sampled.ipynb`, `UNSW-NB15-EDA.ipynb`).
4. Compare metrics (accuracy, balanced accuracy, precision/recall/F1, ROC-AUC, PR-AUC).

## Notes

- Many notebooks process large files; memory usage can be high.
- Some paths are currently hardcoded and may need adjustment for your machine.
- Several methods are unsupervised; results should be interpreted with class imbalance in mind.
- Reproducibility is supported in many cells via `random_state=42`.

## License

This repository is for academic use in COMP9150 Project 2.