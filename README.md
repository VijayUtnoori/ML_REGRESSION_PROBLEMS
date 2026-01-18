# ML_REGRESSION_PROBLEMS

# 📊 House Value Prediction – Regression Models

This project focuses on solving a **regression problem** by predicting house values using machine learning.  
Multiple regression models were trained, evaluated, and compared using consistent preprocessing and evaluation metrics.

The project also demonstrates **outlier handling and skewness correction** to improve model performance.

---

## 📌 Problem Statement
Predict house values based on demographic and housing-related features using regression models and evaluate their performance.

---

## 🛠️ Tech Stack
- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib
- Joblib

---

## 📂 Dataset Overview
- Real-world housing dataset
- Target variable: **House Value (continuous)**
- Contains numerical and categorical features
- Includes skewed distributions and outliers

---

## 🔧 Data Preprocessing & Feature Engineering

### 1️⃣ Missing Values
- Rows with missing values (~1% of data) were safely removed using `dropna()`.

### 2️⃣ Categorical Encoding
- Categorical features encoded using **OneHotEncoder**
- Applied using **ColumnTransformer** for pipeline consistency

### 3️⃣ Outlier & Skewness Handling (IMPORTANT)
To improve model stability and performance:

- **Log Transformation (`log1p`)**
  - Applied to highly skewed numerical features
  - Reduced right-skewness and stabilized variance

- **IQR-based Capping**
  - Used to cap extreme outliers
  - Prevented models from being dominated by extreme values
  - Preserved data while reducing noise

> These techniques significantly improved model generalization, especially for tree-based models.

---

## 🤖 Models Trained

The following regression models were trained using the **same preprocessing pipeline and train-test split**:

1. **Linear Regression**
   - Used as a baseline model
   - Assumes linear relationships

2. **Decision Tree Regressor**
   - Captures non-linear patterns
   - Requires depth control to avoid overfitting

3. **Random Forest Regressor**
   - Ensemble of multiple decision trees
   - Reduces variance and improves generalization
   - Final best-performing model

---

## 📊 Evaluation Metrics

Models were evaluated using regression-specific metrics:

- **R² Score** – Variance explained by the model
- **Mean Absolute Error (MAE)** – Average prediction error
- **Root Mean Squared Error (RMSE)** – Penalizes large errors

---

## 📈 Model Performance Comparison

| Model | R² Score | MAE | RMSE |
|-----|---------|-----|------|
| Linear Regression | 0.64 | 52,939 | 70,319 |
| Decision Tree Regressor | 0.73 | 40,353 | 60,276 |
| Random Forest Regressor | **0.83** | **31,596** | **48,674** |

✅ **Random Forest achieved the best performance**, showing the lowest error and highest explained variance.

---

## 📉 Residual Analysis
- Residual plots were generated for all models
- Random Forest residuals showed:
  - Random scatter around zero
  - No visible patterns
  - Better error distribution compared to LR and DT

This confirms good generalization and reduced bias.

---

## 💾 Model Persistence
All trained models and preprocessing steps were saved using `joblib`:
- Linear Regression model
- Decision Tree model
- Random Forest model
- Preprocessing transformer

This ensures reproducibility and reuse for future predictions or deployment.

---

## 🏆 Conclusion
- Linear Regression underfits due to its linear assumptions
- Decision Tree improves performance but risks overfitting
- Random Forest provides the best balance of bias and variance
- Outlier handling using **Log Transformation + IQR Capping** played a crucial role in improving results

---

## 📌 Key Learnings
- Importance of proper outlier and skewness handling
- Fair model comparison using consistent preprocessing
- Understanding bias–variance tradeoff
- Practical experience with regression workflows

---

## 🚀 Future Improvements
- Hyperparameter tuning using GridSearchCV
- Cross-validation
- Feature importance analysis
- Model deployment using Streamlit or FastAPI
