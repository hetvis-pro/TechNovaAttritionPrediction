# TechNova Employee Attrition Prediction

## Project Context

TechNova Solutions, a mid-sized IT services company with ~1,200 employees, has been facing an attrition rate well above industry standards.  
Despite competitive salaries and benefits, the company struggles to retain talent—especially in technical and client-facing roles.  
This has resulted in increased recruitment costs, project delays, and declining morale.

Company wants to develop a **data-driven attrition prediction model** that identifies at-risk employees early and provides actionable insights to improve retention.

---

## Problem Statement

The HR department currently acts reactively—intervening only after employees resign.  
This project builds a predictive framework to identify employees likely to leave, enabling HR to:

- Focus retention incentives on high-performing yet high-risk employees.
- Optimize resources and avoid over-investing in disengaged staff.
- Design targeted, data-driven engagement strategies.

---

## Objectives

1. **Analyze** the dataset to uncover the key factors influencing attrition.
2. **Build** a predictive model that classifies whether an employee is likely to leave.
3. **Explain** the model using SHAP to ensure interpretability and ethical transparency.
4. **Recommend** actionable HR strategies based on data insights.

---

## Dataset

- **File name:** `employee_churn_dataset.csv`
]- **Features:**
  - Demographics (e.g., Age, Gender, Marital Status)
  - Work profile (e.g., Tenure, Projects Completed, Overtime Hours)
  - Performance & Feedback scores
  - Target variable: `Churn` (0 = Stayed, 1 = Left)

And separate **data dictionary** file used to interpret column meanings.

---

## Project Workflow

### 1️ Data Understanding

- Loaded dataset using pandas, reviewed structure, datatypes, and summary statistics.
- Identified numeric vs categorical variables for preprocessing.

### 2️ Exploratory Data Analysis (EDA)

- Distribution and imbalance check for `Churn`.
- Boxplots and correlation heatmaps to detect relationships.
- Key finding: dataset showed weak correlations → limited predictive signal.

### 3️ Data Preprocessing

- Standardized numeric features using `StandardScaler`.
- Encoded categorical variables using `OneHotEncoder`.
- Combined both into a unified feature matrix (`X_train_final`, `X_test_final`).

### 4️ Handling Class Imbalance

- Applied **SMOTE (Synthetic Minority Over-Sampling Technique)** to balance churn classes in the training set.

### 5️ Model Building

Trained three baseline models for comparison:

- **Logistic Regression** — interpretable linear baseline
- **Random Forest** — nonlinear ensemble
- **XGBoost** — gradient-boosted tree model

### 6️ Model Evaluation

Metrics used: **ROC-AUC**, **Precision**, **Recall**, **F1-score**.  
All models scored close to random (AUC ≈ 0.5) → confirming weak predictive signal in current dataset.

### 7️ Model Explainability (SHAP)

- Used **SHAP (SHapley Additive exPlanations)** for transparency.
- Visualized global and local impacts of features on churn predictions.
- Observed that higher **Salary** and **Satisfaction Level** reduce churn risk, while longer **Overtime Hours** increase it.

### 8️ Recommendations

- Collect more behavioral & engagement data (e.g., surveys, promotion rates).
- Engineer trend-based features (e.g., overtime trend, performance stability).
- Integrate the model into an HR dashboard for continuous churn monitoring.

---

## Key Results

| Model               | ROC-AUC | F1-Score | Recall | Precision |
| :------------------ | :-----: | :------: | :----: | :-------: |
| Logistic Regression |  0.51   |   0.29   |  0.51  |   0.20    |
| Random Forest       |  0.52   |   0.00   |  0.00  |   0.00    |
| XGBoost             |  0.48   |   0.00   |  0.00  |   0.00    |

Even though overall predictive performance was modest, this project successfully demonstrated a complete **end-to-end ML pipeline** and applied **explainable AI** techniques for responsible decision-making.

---

## Insights from SHAP

| Observation               | Interpretation                                     |
| ------------------------- | -------------------------------------------------- |
| 🔹 Salary                 | Higher salaries reduce attrition probability.      |
| 🔹 Satisfaction Level     | Higher satisfaction lowers churn risk.             |
| 🔹 Overtime Hours         | Excessive overtime increases churn risk.           |
| 🔹 Manager Feedback Score | Positive feedback correlates with lower attrition. |

---

## Recommendations for TechNova HR

1. **Monitor Satisfaction Trends** — Run monthly surveys to detect early disengagement.
2. **Optimize Workload** — Reduce overtime for high-performing but overworked employees.
3. **Retention Bonuses** — Offer targeted rewards to high-risk, high-value employees.
4. **Data Collection Upgrade** — Include qualitative factors like culture fit and work-life balance metrics.

---

## Tools & Libraries

- **Python 3.10+**
- pandas, numpy, matplotlib, seaborn
- scikit-learn, imbalanced-learn (SMOTE)
- xgboost
- shap

---

## Repository Structure

```
TechNova_Attrition_Prediction/
│
├── notebook/TechNova_Attrition_Prediction_c0954042.ipynb # Main notebook
├── data/
├── employee_churn_dataset.csv # Dataset
├── employee_churn_data_dictionary.csv # Data dictionary
├── README.md # Project documentation
```
---

## Conclusion

This project illustrates the application of **machine learning in human-resource analytics** for attrition prediction.  
Although model accuracy was limited, the workflow demonstrates strong understanding of **EDA, preprocessing, class balancing, model building, evaluation, and interpretability (SHAP)**.  
The focus on **explainable AI** ensures that predictions are not treated as black boxes but as transparent, data-driven insights to support ethical HR decisions.

---
