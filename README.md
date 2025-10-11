# Stroke Prediction Model

A machine learning project to predict stroke risk using clinical and lifestyle features. This repository covers the complete workflow: data analysis, preprocessing, model training, evaluation, and interpretation.

---

## Introduction

Stroke is a leading cause of mortality and disability. Early risk detection enables preventive healthcare interventions and reduces long-term burdens. This project builds predictive models on a public dataset, aiming to identify individuals at risk of stroke using demographic, clinical, and lifestyle variables, and displays the critical risk factors that causes stokes in individuals using computational methods and data visualization tools.

---

## Data Overview

### 1.1 Dataset

* The dataset contains patient records with both numeric and categorical features relevant to stroke risk.

### 1.2 Target Distribution

- **Stroke = 1 (positive):** 10%
- **Stroke = 0 (negative):** 90%

![Target Distribution](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/images/target_distribution.png)

### 1.3 Features

- **Numeric:** age, average glucose level, BMI
- **Categorical:** gender, residence type, work type, marital status, smoking status

![Histogram: average_glucose_level](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/images/histogram_avg_glucose_level.png)

---

## Methodology

### 2.1 Preprocessing

- **Numeric Features:** Missing values imputed with the median. Features standardized to prevent models (e.g., Logistic Regression) from being biased by scale differences.
- **Categorical Features:** Missing values imputed with the most common category. Encoded using one-hot encoding for efficient model training.
- **Imbalance Handling:** The dataset is imbalanced (1:10 for stroke cases). To address this, models used class weighting to emphasize the minority class.

### 2.2 Models Trained

- **Logistic Regression (balanced weights):** Provides a linear baseline, emphasizing minority stroke cases.
- **Random Forest (class-weighted):** Ensemble of decision trees offering feature importance scores.
- **XGBoost (boosted trees):** Gradient boosting focusing on difficult-to-classify cases.
- **Logistic Regression + SMOTE:** Combines oversampling (SMOTE) with linear classification to improve recall for stroke cases.

---

## Results & Conclusion

### 3.1 Performance Metrics

Primary evaluation metrics:

- **ROC AUC:** Measures the model’s ability to distinguish stroke vs. non-stroke cases.
- **PR AUC:** Focuses on precision and recall for the minority (stroke) class.
- **Confusion Matrix:** Shows counts of true positives, true negatives, false positives, and false negatives.

![ROC AUC: random forest](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/images/roc_curve_rf.png)
![PR AUC : random forest](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/images/pr_curve_rf.png)

### 3.2 Confusion Matrix

The confusion matrix revealed 14 true positives and 37 false negatives for stroke cases.

![Confusion matrix: random forest](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/images/confusion_matrix_rf.png)

### 3.3 Calibration

The calibration curve (Brier score) indicated the model’s probabilities were slightly underconfident.

![Calibration curve: random forest](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/images/calibration_logreg.png)

### 3.4 Feature Importance

Age, blood pressure, and blood glucose were found to be the most significant predictors, aligning with established medical knowledge.

![Feature importance: random forest](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/images/feature_importance_rf.png)

---

## Conclusion
This project demonstrates the development of a stroke prediction model using demographic, lifestyle, and clinical variables. Among all tested methods, the Random Forest classifier performed best, balancing recall and precision. 

However, even with advanced models, some stroke cases remain difficult to identify, as highlighted by the confusion matrix (14 true positives vs. 37 false negatives). This underscores the challenges of predicting rare events in imbalanced datasets.

Feature importance analysis confirmed that age, blood pressure, and blood glucose levels are critical risk factors for stroke, supporting clinical intuition.

By combining performance metrics (ROC/PR AUC), interpretability (feature importance), and diagnostic plots (confusion matrix, calibration curves), this project provides a comprehensive approach for evaluating predictive models in healthcare.
