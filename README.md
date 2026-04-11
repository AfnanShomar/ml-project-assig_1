# Car Evaluation Machine Learning Project

## 📌 Overview

This project aims to predict car prices or acceptability using machine learning techniques. It involves comprehensive preprocessing (including work in Google Sheets), feature engineering, exploratory data analysis, and model evaluation using several algorithms.

---

## 🔄 Workflow Summary

### 📊 **Data Source & Initial Cleanup**
- Original dataset read using:
  ```python
  pd.read_csv('Data/CCar.csv')
  ```
This is after I split the values into rows and fixed the seats column in (CCar.csv)
- The `seats` column contained arithmetic expressions and slash-separated values (e.g., `5/6`, `5+1`), which were:
  - Cleaned in **Google Sheets**
  - Split by rows using the **Power Tools extension** (custom delimiter: `/`)

### 🧹 **Data Preprocessing**
- Dropped duplicate rows.
- Each column was cleaned individually:
  - Columns were **split by spaces or slashes**, and numerical parts were extracted and converted to float.
  - **Missing values** were filled using either the **mean** (for numeric columns) or **mode** (for categorical columns).
- Specific transformations:
  - **Battery Capacity**: Removed "kWh", replaced with `NaN`, and filled with the **mean of Engine CC values** (acknowledging no direct conversion).
  - **Performance**: Standardized units and renamed headers.
  - **Engine**: Split into 3 parts, then all were dropped (not used as features).
  - **Car Name**: Dropped due to high cardinality and low predictive value.
  - **Units** across the dataset were removed for numerical processing.

### 📈 **Exploratory Data Analysis (EDA)** – `Exploratory.ipynb`
- Visualized:
  - **Outliers**
  - **Correlation** between features and price
  - **Relationships** between price and other refined columns
- Tools: `matplotlib`, `seaborn`, and `pandas` visualizations.

### 🧠 **Feature Engineering**
- **One-hot encoding** applied to categorical features like `Fuel Type`.
- Dropped the `seats` column due to **low variance** and **weak predictive power**.

---

## 🤖 Models & Evaluation – `ML_models.ipynb`
- Trained and evaluated the following models:
  - **K-Nearest Neighbors (KNN)**
  - **Support Vector Machine (SVM)**
  - **Random Forest**
- Applied **feature scaling** (`StandardScaler`) where necessary:
  - Especially for KNN and SVM, which are sensitive to scale.
- **Model Insights**:
  - **SVM** performed poorly due to:
    - Feature sensitivity
    - Negative mean values
  - **Random Forest** performed best with:
    - **Lowest average error**
    - Robust performance across all features

---

## ⚙️ Requirements

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

---

## 🚀 How to Run

1. Clean and format raw CSV data in Google Sheets if needed (e.g., split rows on slashes).
2. Run `Preprocessing.ipynb` for cleaning and feature engineering.
3. Run `Exploratory.ipynb` for analysis and visualization.
4. Run `ML_models.ipynb` for model training and evaluation.

---

## 📬 Contact

For improvements, questions, or collaboration, feel free to reach out.
