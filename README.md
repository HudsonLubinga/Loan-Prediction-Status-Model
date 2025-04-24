# 🧠 Loan Prediction Status Model

## 🔍 Project Overview

This project presents a **Machine Learning-based Loan Status Prediction System** built to assist financial institutions in evaluating the likelihood of a loan being approved. Using demographic and financial attributes of applicants, the model predicts whether a loan will be approved (`Y`) or rejected (`N`).

It includes:

- Data cleaning and preprocessing
- Exploratory Data Analysis (EDA)
- Feature engineering
- Multiple classification algorithms with hyperparameter tuning
- Scalable and production-ready API built using **FastAPI**
- Deployment-ready models serialized using `joblib`

---

## 📁 Dataset

The dataset includes 381 loan application records with features such as:

- Applicant Income
- Co-applicant Income
- Loan Amount
- Education Level
- Credit History
- Marital Status, etc.

After removing missing values, 308 cleaned records were used.

---

## 📊 Exploratory Data Analysis (EDA)

Key insights discovered:

- **Applicants with credit history** have significantly higher chances of loan approval.
- **Graduates** tend to receive slightly higher loan amounts.
- **Urban areas** have higher loan approval rates than rural areas.
- **Gender and marital status** also influence loan decisions.

Visualizations included:
- Histograms
- Count plots
- Correlation heatmaps
- Bar charts
- Box plots

---

## ⚙️ Preprocessing Steps

- Label encoding for categorical variables (e.g., `Married`, `Education`)
- Standardization of numerical features using `StandardScaler`
- Removal of null values and data anomalies
- Split into features (`X`) and target (`y`)
- Train-Test split (80:20)

---

## 🧠 Model Building

Three classification algorithms were tested using `GridSearchCV` for hyperparameter optimization:

| Model                | Accuracy Score |
|---------------------|----------------|
| Logistic Regression | 88.7%          |
| K-Nearest Neighbors | 90.3%          |
| Support Vector Machine (SVM) | **90.3%** |

Best parameters for SVM: `C=0.01`, `kernel='linear'`.

---

## 🛠️ FastAPI Deployment

An API was built with **FastAPI** to serve predictions:

**Endpoint:** `/predict/`

**Request Format (JSON):**
```json
{
  "x1": 1,          // Married (Encoded)
  "x2": 4583,       // ApplicantIncome
  "x3": 0,          // Education (Encoded)
  "x4": 128.0,      // LoanAmount
  "x5": 1.0         // Credit_History
}
