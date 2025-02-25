# **Predicting Miscarriage/Stillbirths Using Machine Learning**

## **Overview**
This project aims to develop a **machine learning pipeline** to predict the likelihood of **miscarriage or stillbirths** based on socio-demographic and health-related factors. The model provides **clinical decision support** by identifying high-risk pregnancies and enabling timely interventions.

## **1. Data Acquisition & Preprocessing**
### **Data Sources & Features**
Collected socio-demographic and health-related data, including:
- **Socioeconomic Factors:** Age, education level, household electricity.
- **Demographic & Physiological:** Marital status, BMI, pregnancy history.
- **Medical History:** Chronic conditions (diabetes, hypertension, etc.).
- **Lifestyle:** Smoking, alcohol use, maternal stress levels.

### **Data Cleaning & Handling Missing Values**
- **Imputation:** Applied mean/median imputation for missing values.
- **Feature Reduction:** Removed variables with **>90% missing data**.
- **Low-Variance Filtering:** Excluded features with minimal variation.

### **Class Imbalance Handling**
- Applied **SMOTE (Synthetic Minority Over-sampling Technique)** and **SVMSMOTE** to balance the dataset.

## **2. Feature Selection**
To improve interpretability and reduce overfitting:
- **Lasso Regression:** Identified key predictors by eliminating non-influential features.
- **Ridge Regression:** Addressed multicollinearity among features.

### **Key Features Identified:**
✅ Maternal Age  
✅ Literacy Status  
✅ Pregnancy Complications  
✅ Smoking Status  
✅ Maternal Mental Health  

## **3. Model Development**
Trained multiple machine learning models:
- **Logistic Regression** – Baseline model.
- **Random Forest** – Captured non-linearity but prone to overfitting.
- **Support Vector Classifier (SVC)** – Performed well but computationally expensive.
- **eXtreme Gradient Boosting (XGBoost)** – Best performer.
- **K-Nearest Neighbors (KNN)** – Struggled with high-dimensional data.

## **4. Model Evaluation**
### **Validation Techniques**
✔ **10-fold Cross-Validation** – Ensured generalization.  
✔ **Bootstrapping** – Resampling for robust performance estimates.  

### **Performance Metrics**
| Model | AUC | Accuracy | Precision | Recall | F1 Score |
|-----------|--------|------------|------------|---------|----------|
| Logistic Regression | 0.82 | 0.78 | 0.80 | 0.75 | 0.77 |
| Random Forest | 0.88 | 0.81 | 0.85 | 0.79 | 0.82 |
| Support Vector Classifier | 0.87 | 0.80 | 0.83 | 0.78 | 0.80 |
| **XGBoost (Best Model)** | **0.90** | **0.85** | **0.88** | **0.80** | **0.83** |
| KNN | 0.75 | 0.72 | 0.70 | 0.65 | 0.67 |

## **5. Model Interpretation using SHAP Analysis**
To improve interpretability, **SHAP (SHapley Additive exPlanations)** was used to explain feature importance.

### **Key Feature Contributions:**
📌 **BMI** – Higher BMI linked to increased risk.  
📌 **Smoking & Alcohol Consumption** – Strong negative impact.  
📌 **Maternal Stress Levels** – Higher stress increased risk.  
📌 **Age** – Higher risk for very young (<18) or older (>35) mothers.  

## **6. Conclusion & Recommendations**
✅ **Clinical Application:** Can be deployed as a **decision-support tool** for healthcare providers.  
✅ **Early Intervention:** High-risk patients can receive **targeted counseling and interventions**.  
✅ **Feature Refinement:** Future data collection (e.g., genetic factors, blood biomarkers) can improve accuracy.  
✅ **Ethical Considerations:** Must ensure fairness across different socio-demographic groups.  

## **7. Future Enhancements**
🚀 **Deep learning approaches** – LSTMs for temporal pregnancy data.  
🚀 **Integration with EHR systems** – Real-time risk assessment.  
🚀 **Intervention modeling** – Assess lifestyle changes' impact.  


