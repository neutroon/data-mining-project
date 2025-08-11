
## Lung Cancer Dataset – End‑to‑End EDA, Preprocessing, and Baseline Models

### Project overview

End‑to‑end workflow on a large lung cancer dataset (~890k rows): exploratory data analysis, outlier analysis, feature engineering, robust preprocessing with a `ColumnTransformer`, baseline model training (Logistic Regression and Random Forest), evaluation, and feature importance review — all implemented in `notebook.ipynb`.

### Dataset

- **Demographics**: `age`, `gender`, `country`
- **Clinical**: `cancer_stage`, comorbidities (`hypertension`, `asthma`, `cirrhosis`, `other_cancer`), `treatment_type`, `bmi`, `cholesterol_level`
- **Timeline**: `diagnosis_date`, `end_treatment_date`
- **Target**: `survived` (0 = No, 1 = Yes)

Source: [Kaggle – Lung Cancer Dataset](https://www.kaggle.com/datasets/khwaishsaxena/lung-cancer-dataset)

### What’s implemented in the notebook

1) Data loading and quick EDA
- Load CSV with pandas
- Preview (`head`), schema (`info`), summary stats (`describe`)
- Target exploration: class counts for `survived`

2) Outlier analysis and optional removal
- IQR‑based detector over numeric columns with per‑column bounds and counts
- Utility to remove rows outside IQR bounds (kept optional; main ML pipeline uses the original data copy)

3) Normalization for inspection
- `MinMaxScaler` applied to numeric columns to examine scaled distributions (used for analysis, not fed to the models)

4) Feature engineering
- `treatment_duration_days` computed as `end_treatment_date - diagnosis_date` (in days)
- Visualizations: histogram and boxplot for distribution and spread

5) ML preprocessing pipeline
- Drop non‑informative columns: `id`, `country`
- Automated type detection for `numeric_cols` and `categorical_cols`
- `ColumnTransformer` with two pipelines:
  - Numeric: `SimpleImputer(strategy='mean')` → `StandardScaler`
  - Categorical: `SimpleImputer(strategy='most_frequent')` → `OneHotEncoder(handle_unknown='ignore')`
- Datetime columns are not modeled directly and are excluded from the transformer; engineered durations are used instead

6) Train/test split
- 80/20 split with `random_state=42` (stratification used where applicable during exploration; model pipeline uses the standard split)

7) Baseline modeling and evaluation
- Logistic Regression (`max_iter=1000`)
- Random Forest (`n_estimators=100`, `random_state=42`, `n_jobs=-1` for parallel training)
- Metrics: accuracy on the hold‑out test set for both models
- Random Forest feature importance with aligned feature names (`numeric` + one‑hot categorical)


### Project structure

- `Lung Cancer.csv` — dataset
- `notebook.ipynb` — complete analysis, preprocessing, models, and visuals
- `Titanic.ipynb` — separate, unrelated example notebook
- `Lung Cancer Dataset.docx`, `Lung Cancer Dataset.pdf` — dataset documentation
- `README.md` — this document

### Notes and considerations

- Dataset is large; expect multi‑minute training without a strong CPU/RAM. Parallelism is enabled for Random Forest.
- Class imbalance may affect accuracy; consider additional metrics (precision/recall/ROC‑AUC) in future iterations.
- `ColumnTransformer` ensures reproducible, consistent preprocessing across splits and models.

### Contributors

- Hesham Mansour
- Hosny Almasrii

### References

- [Kaggle – Lung Cancer Dataset](https://www.kaggle.com/datasets/khwaishsaxena/lung-cancer-dataset)
- [GitHub](https://github.com/neutroon/data-mining-project)
