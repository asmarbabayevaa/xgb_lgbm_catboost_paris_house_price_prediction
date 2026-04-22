# xgb_lgbm_catboost_paris_house_price_prediction
A complete regression pipeline comparing three leading gradient boosting frameworks on the Paris house prices dataset. The project covers baseline modelling, hyperparameter tuning with Optuna, and model interpretability using feature importance and SHAP values.

## Project Overview

This notebook benchmarks **XGBoost**, **LightGBM**, and **CatBoost** on a structured regression task — predicting house prices in Paris. It goes beyond simple model training by adding systematic hyperparameter search and post-hoc explainability to understand what drives price predictions.



## Dataset

- **File:** `paris_house_prices.xlsx`
- **Target:** `price`
- **Features:** Square footage, number of rooms, yard, pool, new build status, storm protector, storage room, and more
- **Note:** This is a synthetic dataset commonly used for ML practice. Real-world results would differ.


##  Pipeline

1. **EDA** — Descriptive statistics and null value check
2. **Preprocessing** — Label encoding for categorical columns; raw data preserved for CatBoost's native categorical handling
3. **Baseline Models** — Default parameters for XGBoost, LightGBM, CatBoost (standard + categorical variant)
4. **Hyperparameter Tuning** — Optuna with 5-fold cross-validation; 50 trials for LightGBM & XGBoost, 30 for CatBoost
5. **Final Comparison** — All models ranked by Test R², with an overfitting gap column (`Train R² − Test R²`)
6. **Feature Importance** — Normalized importance scores from the best LightGBM model
7. **SHAP Analysis** — Summary plot for features with importance between 1%–35%
8. **Feature-Selected Final Model** — LightGBM re-tuned on the most informative features only

## Key Results

> ⚠️ High R² scores (~0.99) are expected on this dataset due to its synthetic nature. The pattern between features and price is mathematically clean, which tree-based models exploit very effectively. This does not reflect real-world performance.

The R² Gap column in the final review table is a useful indicator of how much each model overfits — lower is better.

