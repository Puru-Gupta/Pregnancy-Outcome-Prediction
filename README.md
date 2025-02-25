# **Predicting Miscarriage/Stillbirth Risk Using Machine Learning**

## **1. Problem Statement & Objective**
This project aims to develop a **machine learning pipeline** for predicting the likelihood of **miscarriage or stillbirth** based on socio-demographic and health-related factors. The objective is to enhance **clinical decision support** by identifying high-risk pregnancies early, enabling timely interventions.

---

## **2. Data Acquisition & Preprocessing**

### **Data Sources & Variables**
The dataset includes socio-demographic, maternal health, and lifestyle factors such as:
- **Demographics:** Age, education level, household electricity.
- **Physiological Factors:** Marital status, BMI, pregnancy history.
- **Health Conditions:** Chronic diseases (diabetes, hypertension), lifestyle habits (smoking, alcohol use).
- **Maternal Mental Health:** Stress levels and psychological well-being.

### **Data Cleaning & Handling Missing Values**
- **Imputation:** Missing values handled using mean, median, or mode.
- **Feature Reduction:** Variables with **>90% missing values** were removed.
- **Low-Variance Filter:** Features with minimal variation were excluded.

### **Class Imbalance Handling**
- Used **SMOTE (Synthetic Minority Over-sampling Technique)** and **SVMSMOTE (Support Vector Machine SMOTE)** to address class imbalance in pregnancy outcomes.

---

## **3. Feature Selection**
To improve model interpretability and reduce overfitting, the following techniques were applied:
- **Lasso Regression:** Shrinks coefficients of less important features to zero.
- **Ridge Regression:** Reduces collinearity among features.

### **Key Predictive Features Identified:**
- **Maternal Age** (Higher risk for very young or older mothers).
- **Literacy Status** (Education affects access to healthcare and risk awareness).
- **Pregnancy Complications** (Previous adverse pregnancy outcomes increase risk).
- **Smoking Status** (Strongly linked to fetal development issues).
- **Maternal Mental Health** (Stress and depression contribute to complications).

---

## **4. Model Development**
Multiple machine learning models were trained and evaluated:

| **Model**                 | **Description** |
|---------------------------|----------------|
| **Logistic Regression**   | Baseline model, interpretable but limited in handling complex patterns. |
| **Random Forest**         | Captures non-linearity but prone to overfitting. |
| **Support Vector Classifier (SVC)** | Performs well but computationally expensive. |
| **eXtreme Gradient Boosting (XGBoost)** | Handles feature interactions well and provides strong predictive performance. |
| **K-Nearest Neighbors (KNN)** | Struggles with high-dimensional data. |

---

## **5. Model Evaluation**
### **Validation Techniques**
- **10-fold Cross-Validation:** Ensures generalization across different data splits.
- **Bootstrapping:** Provides robust estimates by resampling data.

### **Performance Metrics Used**
- **AUC (Area Under the Curve)** – Model's ability to distinguish between cases.
- **Accuracy** – Overall correctness.
- **Precision (Positive Predictive Value)** – % of predicted high-risk cases that were truly high-risk.
- **Recall (Sensitivity)** – % of actual high-risk cases correctly identified.
- **F1 Score** – Balance between Precision & Recall.
- **Specificity** – Ability to correctly classify non-high-risk cases.

### **Model Performance**

| **Model**        | **AUC** | **Accuracy** | **Precision** | **Recall** | **F1 Score** |
|-----------------|--------|------------|------------|---------|----------|
| Logistic Regression | 0.82 | 0.78 | 0.80 | 0.75 | 0.77 |
| Random Forest | 0.88 | 0.81 | 0.85 | 0.79 | 0.82 |
| Support Vector Classifier | 0.87 | 0.80 | 0.83 | 0.78 | 0.80 |
| **XGBoost (Best Model)** | **0.90** | **0.85** | **0.88** | **0.80** | **0.83** |
| KNN | 0.75 | 0.72 | 0.70 | 0.65 | 0.67 |

**Best Model: XGBoost with SMOTE & Ridge Regression**
- **AUC: 0.90** → High discriminatory power.
- **Accuracy: 0.85** → Well-balanced performance.
- **Precision: 0.88** → Model reliably identifies high-risk pregnancies.
- **Recall: 0.80** → 80% of actual miscarriage/stillbirth cases were correctly predicted.
- **F1 Score: 0.83** → Good balance between precision and recall.

---

## **6. Model Interpretation using SHAP Analysis**
To enhance interpretability, **SHAP (SHapley Additive exPlanations)** analysis was used to explain feature importance:

### **Key Feature Contributions:**
- **BMI:** Higher BMI linked to increased risk.
- **Smoking & Alcohol Consumption:** Strong negative impact on pregnancy outcomes.
- **Maternal Stress Levels:** Higher stress increased the likelihood of miscarriage/stillbirths.
- **Age:** Both very young (<18) and older mothers (>35) had elevated risks.

SHAP analysis helped clinicians understand why certain predictions were made, making the model more **transparent and actionable**.

---

## **7. Conclusion & Recommendations**
- **Early Intervention:** High-risk patients can receive **targeted counseling and interventions**.
- **Feature Refinement:** Further improvements in data collection (e.g., genetic factors, blood biomarkers) may enhance prediction accuracy.
- **Ethical Considerations:** Ensure fairness across socio-demographic groups and avoid unnecessary anxiety for patients.

---
