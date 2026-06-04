# DK1 Day-Ahead Price Forecasting Thesis Artifacts

## Contents

- `notebooks/da-experiments-fs4-rerun.ipynb`  
  Cleaned final experiment notebook for the price task. It contains the model
  setup, feature sets, baselines, LEAR baseline, Optuna search logic, TabNet
  rerun integration, and final artifact export code. Notebook outputs have been
  stripped for public sharing.

- `notebooks/results-visualization.ipynb`  
  Cleaned analysis notebook for result tables, figures, SHAP analysis, and
  Diebold-Mariano tests. It reads the artifact files in `artifacts/`.

- `artifacts/test_predictions_df.parquet`  
  Final test-set predictions. The file contains the actual DK1 day-ahead price
  and predictions for 105 models/baselines over the test window.

- `artifacts/results_df.parquet`  
  Final aggregate result table with 105 rows. Public test metrics were
  recalculated from `test_predictions_df.parquet` so the result table and
  prediction artifact are internally consistent.

- `artifacts/results_df.csv`  
  CSV mirror of `results_df.parquet` for easier inspection on GitHub.

## Headline Result

The best final configuration is `lgbm_fs4_wp`, a LightGBM model using the FS4
feature set and wrapper-selected feature groups with the sparsity penalty.

| Model | MAE | RMSE | R2 |
| --- | ---: | ---: | ---: |
| `lgbm_fs4_wp` | 14.521775 | 19.531920 | 0.885031 |
| `xgb_fs4_wp` | 15.111032 | 19.948483 | 0.880074 |
| `tabnet_fs4_np` | 25.016015 | 32.402646 | 0.683588 |
| `lear` | 30.800692 | 39.168360 | 0.533462 |
