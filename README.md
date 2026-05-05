# Predicting Pump.fun Token Graduation: A Random Forest Tutorial

This repository contains a notebook tutorial for predicting whether Pump.fun tokens graduate using early trading behavior and a Random Forest classifier.

The project focuses on the practical machine-learning problem created by severe class imbalance: most Pump.fun tokens fail, so raw accuracy is misleading. The notebook walks through feature engineering, stratified train/test splitting, class-weighted model training, precision/recall evaluation, feature importance, and a graduation watchlist.

## Repository Contents

- `Predicting Pump.fun Token Graduation A Random Forest.ipynb` - end-to-end tutorial notebook.
- Accompanying article: https://medium.com/p/9ef8da928390
- `requirements.txt` - Python dependencies for running the notebook.
- `.gitignore` - excludes local data files, virtual environments, and generated artifacts.

## Data

The notebook expects the following CSV files in the repository root:

- `train.csv`
- `chunk_1.csv`

These files are not included because they are dataset artifacts. Download them from Kaggle:

https://www.kaggle.com/datasets/dremovd/pump-fun-graduation-february-2025

Place both CSV files next to the notebook before running it.

## Setup

Create a virtual environment and install dependencies:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

On Windows PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

## Run The Tutorial

Start Jupyter and open the notebook:

```bash
jupyter notebook "Predicting Pump.fun Token Graduation A Random Forest.ipynb"
```

Run the notebook cells in order after placing `train.csv` and `chunk_1.csv` in the repository root.

## Method Summary

The tutorial builds token-level behavioral features from early swaps, including:

- Total swaps
- Unique wallets
- Buy/sell ratio
- Average swap size
- Whale score
- Capital efficiency
- Token age
- Total fees

It trains a `RandomForestClassifier` with `class_weight='balanced'` to address the extreme imbalance between failed and graduated tokens.

## Evaluation Focus

For this use case, precision is prioritized over recall because false positives can represent capital loss, while false negatives are missed opportunities. The notebook therefore emphasizes classification reports, confusion matrices, precision-recall curves, ROC-AUC, and feature importance rather than raw accuracy alone.

## Limitations

- The model uses historical data and is not a live trading system.
- The included feature set is based on early observed token behavior only.
- Results depend on the specific Kaggle data snapshot and preprocessing choices.
