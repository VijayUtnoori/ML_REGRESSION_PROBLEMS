# 📊 House Value Prediction – Regression Models

This project focuses on solving a **regression problem** by predicting house values using machine learning.  
Multiple regression models were trained, evaluated, and compared using a consistent preprocessing pipeline and evaluation metrics.

The project also demonstrates **outlier handling at both feature and target levels** and analyzes its impact on different regression models.

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
- Includes skewed feature distributions and target outliers

---

## 🔧 Data Preprocessing & Feature Engineering

### 1️⃣ Missing Values
- Rows with missing values (~1% of data) were safely removed using `dropna()`.

### 2️⃣ Categorical Encoding
- Categorical features were encoded using **OneHotEncoder**
- Implemented via **ColumnTransformer** for pipeline consistency

### 3️⃣ Outlier & Skewness Handling

#### 🔹 Feature-Level Handling
To improve model stability:

- **Log Transformation (`log1p`)**
  - Applied to highly skewed numerical feature columns
  - Reduced right-skewness and stabilized feature distributions

- **IQR-based Capping**
  - Applied to numerical feature outliers
  - Reduced the influence of extreme values

#### 🔹 Target-Level Handling (Experiment)
- **IQR-based capping was applied to the target variable**
- This experiment was performed to study the sensitivity of different models to target outliers

📌 **Observation:**
- Linear Regression showed a **measurable improvement**
- Decision Tree and Random Forest showed **minimal change**, indicating robustness to target outliers

---

## 🤖 Models Trained

All models were trained using the **same preprocessing pipeline and train–test split**.

1. **Linear Regression**
   - Highly sensitive to outliers
   - Benefited from target IQR-based capping

2. **Decision Tree Regressor**
   - Captures non-linear relationships
   - Naturally robust to outliers

3. **Random Forest Regressor**
   - Ensemble of decision trees
   - Strong generalization and outlier robustness
   - Best-performing model overall

---

## 📊 Evaluation Metrics

- **R² Score** – Variance explained by the model
- **Mean Absolute Error (MAE)** – Average absolute prediction error
- **Root Mean Squared Error (RMSE)** – Penalizes large errors

---

## 📈 Model Performance Comparison (After Target IQR Capping)

| Model | R² Score | MAE | RMSE |
|------|----------|-----|------|
| Linear Regression | **0.64** | **51,918** | **68,610** |
| Decision Tree Regressor | 0.73 | 40,353 | 60,276 |
| Random Forest Regressor | **0.83** | **31,596** | **48,674** |

📌 **Key Insight:**  
Target IQR-based capping improved Linear Regression performance, while Decision Tree and Random Forest remained largely unchanged due to their inherent robustness to outliers.

---

## 📉 Residual Analysis
- Residual plots were generated for all models
- Random Forest residuals showed:
  - Random scatter around zero
  - No systematic patterns
  - Better error distribution compared to LR and DT

This confirms good generalization and reduced bias.

---

## 💾 Model Artifacts & Reproducibility
- Trained model files (`.pkl`) were generated locally
- Due to GitHub file size limits, model artifacts are excluded from version control
- A `.gitignore` file is used to prevent accidental commits of large files

📌 All results are **fully reproducible** by running the notebook.

---

## 🏆 Conclusion
- Linear Regression benefited from **target-level IQR-based outlier handling**
- Decision Tree and Random Forest were largely unaffected due to robustness
- Random Forest achieved the best overall performance
- Outlier handling experiments provided valuable insights into model sensitivity

---

## 📌 Key Learnings
- Linear models are sensitive to target outliers
- Tree-based models are naturally robust
- Outlier handling should be evaluated empirically
- Fair model comparison requires consistent preprocessing

---

## 🚀 Future Improvements
- Hyperparameter tuning using GridSearchCV
- Cross-validation
- Feature importance analysis
- Model deployment using Streamlit or FastAPI
