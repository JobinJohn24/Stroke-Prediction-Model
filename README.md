# 🩻🩺 Stroke Prediction Model 🩻🩺

## 📋 Abstract  
This research implements machine learning methodologies to develop a predictive model for stroke risk assessment utilizing clinical and demographic features. The study addresses the critical healthcare challenge of early stroke detection through advanced statistical modeling and machine learning techniques.

## 📝 Methodology  

### Data Characteristics  
The dataset comprises heterogeneous patient records with continuous and categorical variables. The target variable exhibits class imbalance with a 1:10 ratio of stroke to non-stroke cases, as illustrated in Figure 1.

![Target Distribution](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/images/target_distribution.png)
*Figure 1: Distribution of target variable demonstrating class imbalance*

### Feature Analysis
The dataset includes both continuous and categorical variables:
- **Continuous Variables:** age, average glucose level, BMI  
- **Categorical Variables:** gender, residence type, work type, marital status, smoking status  

Distribution analysis of key continuous variables revealed significant patterns, as shown in Figure 2.

![Histogram: average_glucose_level](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/images/histogram_avg_glucose_level.png)
*Figure 2: Distribution of average glucose levels across the patient population*

### Feature Engineering  
- **Continuous Variables:**
  - Standardization applied  
  - Missing value imputation via median substitution  
- **Categorical Variables:**
  - One-hot encoding implementation  
  - Mode-based imputation for missing values  

### Model Development  
Multiple classification algorithms were evaluated:  
1. Logistic Regression with balanced class weights  
2. Random Forest with class-weight optimization  
3. XGBoost with gradient boosting  
4. Synthetic Minority Over-sampling Technique (SMOTE) combined with Logistic Regression

## 📊 Results  

### Performance Evaluation  
Models were assessed using multiple metrics, with the Random Forest classifier's performance illustrated in Figures 3 and 4.

![ROC AUC: random forest](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/images/roc_curve_rf.png)
*Figure 3: ROC curve demonstrating model discrimination capability*

![PR AUC : random forest](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/images/pr_curve_rf.png)
*Figure 4: Precision-Recall curve highlighting model performance on imbalanced data*

### Classification Results
The confusion matrix (Figure 5) provides detailed insight into the model's classification performance.

![Confusion matrix: random forest](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/images/confusion_matrix_rf.png)
*Figure 5: Confusion matrix showing classification outcomes*

### Model Calibration
Probability calibration analysis (Figure 6) revealed slight underconfidence in probability estimates.

![Calibration curve: random forest](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/images/calibration_logreg.png)
*Figure 6: Calibration curve showing probability estimation reliability*

### Feature Attribution  
Analysis revealed age, blood pressure, and glucose levels as primary predictive indicators, consistent with established clinical literature (Figure 7).

![Feature importance: random forest](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/images/feature_importance_rf.png)
*Figure 7: Feature importance rankings from Random Forest classifier*

## 👨‍💻 Conclusions  
The Random Forest classifier demonstrated superior performance in balancing sensitivity and specificity. However, the identification of certain stroke cases remains challenging, as evidenced by the confusion matrix metrics (14 true positives versus 37 false negatives). The study's findings contribute to the growing body of literature on machine learning applications in preventive healthcare.

The research highlights the potential and limitations of machine learning in clinical prediction tasks, suggesting areas for future investigation in feature engineering and model optimization.
