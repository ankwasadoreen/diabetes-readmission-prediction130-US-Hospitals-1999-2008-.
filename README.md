# Project Overview

Hospital readmission among diabetic patients is a major healthcare challenge, leading to increased costs and adverse patient outcomes.
This project develops and evaluates supervised machine learning models to predict 30-day hospital readmission using the Diabetes 130-US Hospitals (1999–2008) dataset.

The task is formulated as a binary classification problem, where:
1 = Readmitted within 30 days
0 = Not readmitted within 30 days

The goal is to support risk stratification and enable early clinical intervention.



# Dataset

Source: Diabetes 130-US Hospitals Dataset (1999–2008)

Records: 100,000+ hospital encounters

Features: Demographics, diagnoses, lab results, medications, utilization history

Outcome: 30-day hospital readmission

Dataset obtained from the UCI Machine Learning Repository.
Patient and encounter identifiers were removed to prevent data leakage.




# Data Preparation

Removed identifiers and low-information variables

Handled high-cardinality diagnosis codes to reduce noise

Converted categorical variables to factors

Retained numeric variables at original scale

 class imbalance (~11% readmitted)

Train/Test split: 80% / 20%
 

##  Methodology
- Data cleaning and preprocessing
- Handling missing values and categorical encoding
- Feature engineering
- Remember: Class imbalance handling
- Model training and evaluation


# Modeling Methods

Five supervised classification models were implemented and compared:

Ridge Logistic Regression – Regularized linear model emphasizing coefficient stability

LASSO Logistic Regression – Regularized model with automatic feature selection

Random Forest – Bagging-based ensemble of decision trees

LightGBM – Efficient gradient boosting framework

XGBoost – Boosting-based ensemble with class-imbalance weighting

These models represent a range of linear vs. nonlinear, regularized, and ensemble-based approaches.



# Evaluation Metrics

To account for class imbalance, multiple metrics were used:

- Accuracy

- AUC (ROC)

- Sensitivity (Recall)

- Specificity

- Balanced Accuracy

# Model Comparison
| Model          | AUC       | Balanced Accuracy | Notes                 |
| -------------- | --------- | ----------------- | --------------------- |
| LASSO Logistic | 0.626     | 0.580             | Sparse, interpretable |
| Ridge Logistic | 0.621     | 0.583             | Stable coefficients   |
| Random Forest  | 0.588     | 0.569             | Weaker discrimination |
| LightGBM       | 0.628     | 0.586             | Efficient boosting    |
| **XGBoost**    | **0.681** | **0.628**         | **Best overall**      |


# Final Model Selection

XGBoost was selected as the final model due to its superior performance in this highly imbalanced clinical setting.

AUC: 0.681

Improved discrimination using class-weighted training

Outperformed linear and other ensemble methods

# Key Predictors Identified

Across models, the most influential predictors included:

Number of prior inpatient admissions

Length of hospital stay

Number of medications

Emergency and outpatient visits

Diabetes-related medication changes

Laboratory indicators (e.g., A1C results)

These predictors align with clinical intuition and healthcare utilization patterns.

# Data Visualization

Distribution of hospital length of stay (right-skewed)

Distribution of prior inpatient admissions (strong class imbalance)

ROC curve for weighted XGBoost model


# Tools & Technologies

Language: R

Libraries: tidyverse, caret, ggplot2, xgboost, randomForest

Techniques: Supervised learning, regularization, ensemble methods, imbalanced classification

#  Limitations

Readmission events are rare, limiting predictive performance

Diagnosis variables were simplified

Social determinants of health not available.


# Future Work

Temporal and longitudinal modeling

Advanced resampling or cost-sensitive learning

Explainability methods (e.g., SHAP values)

Integration of socioeconomic and external clinical data

#  Key Takeaways

Predicting readmission is challenging due to patient heterogeneity and class imbalance

Linear models provide interpretability but limited discrimination

Ensemble tree-based methods outperform linear approaches

Machine learning–based risk stratification shows promise for clinical decision support


All analytical code is provided separately as supplemental materials in accordance with project guidelines.

