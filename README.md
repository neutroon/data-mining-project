
# Lung Cancer Dataset – Data Exploration & Preprocessing

## 📌 Project Overview

This project focuses on the **exploration and preprocessing** of the [Lung Cancer Dataset](https://www.kaggle.com/datasets/khwaishsaxena/lung-cancer-dataset). It is part of a final project task that includes cleaning, transforming, and preparing the dataset for future machine learning use.

---

## 📁 Dataset Description

The dataset includes patient-level data such as:

- **Demographics**: age, gender, country
- **Medical details**: cancer stage, comorbidities, treatment type
- **Timeline**: diagnosis date and treatment end date
- **Target variable**: `survived` (0 = No, 1 = Yes)

---

## ✅ Tasks Completed

### 1. **Data Loading**
- Dataset loaded using `pandas.read_csv()`
- Handled missing values by detecting `?` as `NaN`

### 2. **Exploratory Data Analysis**
- Displayed first 5 rows
- Inspected datatypes and value distributions
- Examined missing values per column

### 3. **Missing Value Handling**
- Identified and filled missing values using:
  - **Median** for numeric features
  - **Mode** for categorical features (optional)

### 4. **Outlier Detection and Handling**
- Used the **IQR method** to detect outliers in numeric columns
- Applied two methods:
  - **Removal** of rows containing outliers
  - **Capping (Winsorization)** to clip outlier values to valid range

### 5. **Feature Scaling**
- Applied **Min-Max Normalization** to scale numeric features between 0 and 1 using `MinMaxScaler`
- Standardization using `StandardScaler` is supported (not the default)

### 6. **Train/Test Split**
- Separated data into **features (`X`)** and **target (`y`)**
- Encoded categorical variables using `pd.get_dummies()`
- Split into training and testing sets using `train_test_split()` with `stratify=y` for balanced classes

### 7. **Feature Engineering**
- Created a new column: `treatment_duration_days` by calculating:
  ```
  treatment_end_date - diagnosis_date
  ```
- Visualized this feature using a **boxplot** to analyze its spread and detect any anomalies

---

## 📊 Visualizations

- Boxplot of `treatment_duration_days` to analyze distribution
- (Optional) Histogram and additional plots can be added for deeper insights

---

## 🛠 Technologies Used

- Python 3.x
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn

---

## 📂 Files Included

- `Lung Cancer.csv` – Original dataset
- `notebook.ipynb` / `preprocessing.py` – Python code for all steps
- `report.docx` – Word report with explanation and screenshots
- `report.pdf` – PDF version of the report
- `README.md` – This file

---

## 🧠 Future Work

- Train machine learning models (Logistic Regression, Decision Trees, etc.)
- Evaluate using accuracy, precision, recall
- Apply further feature selection or dimensionality reduction (e.g., PCA)

---

## 👥 Contributors

- Hesham Mansour  
- Hosny Almasrii

---

## 📎 References

- [Kaggle Dataset](https://www.kaggle.com/datasets/khwaishsaxena/lung-cancer-dataset)
