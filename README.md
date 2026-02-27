# NBA Performance Forecasting

# NBA Player Performance Forecasting  
Workload & Rolling Form-Based Modeling

## Project Overview

This project builds a performance forecasting pipeline using NBA game log data retrieved via `nba_api`. The goal is to predict short-term player performance using rolling form and workload-derived features while preventing data leakage through time-aware evaluation.

This workflow mirrors performance analytics applications in professional basketball, including load management, volatility tracking, and short-term game outcome forecasting.

---

## Feature Engineering

Engineered signals include:

- Rolling 5-game and 10-game averages (PTS, MIN, AST, REB, TOV)
- 10-game scoring volatility (standard deviation)
- Rest days between games
- Back-to-back indicator
- Recent workload trends

All features are calculated using only prior games to avoid leakage.

---

## Modeling Tasks

### Regression
Target: Next-game points  
Model: Ridge Regression baseline  
Evaluation: Time-based holdout split  

### Classification
Target: Will player exceed rolling 10-game scoring average next game?  
Model: Logistic Regression (class-balanced)  
Evaluation: ROC-AUC, PR-AUC, accuracy, precision, recall  

---

## Results (Example Output)

Regression:
- MAE: ~5 points  
- R²: ~0.50  

Classification:
- ROC-AUC: ~0.70  
- PR-AUC: ~0.68  

Rolling 10-game scoring average and minutes workload were the strongest predictive features.

---

## Practical Applications

This framework supports:

- Short-term performance forecasting  
- Load management decision support  
- Identifying high-variance players  
- Game-planning adjustments based on fatigue proxies  

The modular pipeline can be extended to multi-season modeling or injury risk forecasting.

---

## Reproducibility

All artifacts are generated programmatically via:

python -m src.pull_player_gamelogs  
python -m src.build_dataset  
python -m src.train  

Raw and processed datasets are excluded from version control to maintain repository hygiene.
