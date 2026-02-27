# Model Reports & Outputs

This directory contains model artifacts generated after running the NBA Performance Forecasting pipeline locally.

These outputs are intentionally lightweight and reproducible. Raw and intermediate data files are excluded from version control to maintain a clean, professional repository structure.

---

## Generated Artifacts (Created After Training)

When the following commands are executed:

python -m src.train --season 2024-25 --task regression  
python -m src.train --season 2024-25 --task classification  

The pipeline produces:

### 1️⃣ Evaluation Metrics
- `metrics_regression_*.json`
- `metrics_classification_*.json`

These files include:
- MAE and R² (regression)
- ROC-AUC, PR-AUC, accuracy, precision, recall (classification)
- Train/test sample counts

---

### 2️⃣ Feature Importance
- `feature_importance_*.csv`

Permutation importance is used to quantify the contribution of rolling workload and performance signals.

---

### Visualizations (Optional to Commit)
- `figures/featimp_*.png`

Feature importance plots can be committed to the repository for quick visual review by analysts and recruiters.

---

## Reproducibility

All reports are generated programmatically via:

python -m src.train

No manual post-processing is required.

---

## Portfolio Design Note

Only essential visual outputs are intended for GitHub upload.  
JSON and CSV artifacts are kept local to:

- Avoid repository clutter  
- Follow professional data science repository standards  
- Maintain reproducibility best practices  
