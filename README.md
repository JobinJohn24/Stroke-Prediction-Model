# Stroke Prediction Model
A machine learning project to predict stroke risk using clinical and lifestyle features. This repository walks though the complete workflow: data analysis, preprocessing, model training, evaluation interpretability, and calibration

# Introduction
Stroke is the leading cause of mortaility and disbaility. early risk detection can enable preventive healthcare intervention and reduce long-term burden. This project builds predictive models on a public healthcare dataset to classify patients as at risk of stroke (stroke = 1) or not (stroke = 0).

Data Overview

## 1.1 
Dataset: 

## 1.2 Target distribution
* Stroke = 1 (positive): 10%
* Stroke = 0 (negative): 90%

![Target Distribution](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/target_distribution.png)

1.3 Features 
* Numeric features: age, average glucose level, BMI
* Categorical features: gender, residence type, work type, marital status, smoking status
* ![Histogram: average_glucose_level](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/histogram_avg_glucose_level.png)

# Methodology
## 2.1 Preprocessing
* Numeric features: Missing values were imputed using the median, the features were standarized to make sure models such as Logistic Regression weren't numerical biased on scale differences ie glucose vs age
* Categorical features: Missing values were imputed with the most common category, then turned into a one-hot encoding (y/n) so the model training and splitting would be efficent.
* Imbalance handling: The dataset established a precedent of 1 in 10 patients actually having/had a stroke, the dataset was skewed to account for the "no stroke." To fix the issue, class weights (modifying the models loss function to account for a larger penalty comparitive to the errors on the non-stroke cases) and SMOTE (Synthetic Minority Over Sampling Technique - generating minority samples and interpolating between existing ones in feature space) techniques were used.

## 2.2 Models trained
* Logistic Regession (balanced weights): interpreting a linear baseline by emphasizes minority stroke cases which makes it a fair standing benchmark.
* Random Forest (class-weighted): A collection of decision trees that provide feature importance scores, which indicate which variables attirbute to the most stroke risk.
* XGBoost (boosted trees): A grident boosting algorithm, which focuses on the hardest to classify cases.
* Logistic Regression + SMOTE: A combination of oversampling and linear classifying, testing whether it has the ability to catch more stroke cases without sacrificing efficeny.

# Results & Conclusion
## 3.1 Performance Metrics
To find the true measurement of true postives, true negative, and the amount of precision is by using the ROC AUC (receiver operating characteristic area under curve), and the PR AUC (precision-recall area under curve)

* The ROC AUC is used to measure the distinguishing model factors or stroke vs non-stroke cases
* The PR AUC is used to measure the minority class, in this case is the stroke-inducing cases. Showing how efficent the model maintained precision while also increasing recall.
* The confusion matrix is used to measure how many cases within the dataset have been true positive, negatives, and false negatives.

![ROC AUC: random forest](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/roc_curve_rf.png)
![PR AUC : random forest](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/pr_curve_rf.png)

## 3.2 Confusion Matrix
The confusion matrix indicated 14 true positives vs. 37 false negatives

![confusion matrx: random forest](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/confusion_matrix_rf.png)

## 3.3 Calibration
The calibration curve provides a brier score indicating that it has underconfident probablities 
![calibration curve: random forest](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/calibration_logreg.png)

## 3.4 Feature Importance
![feature importance: random forest](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/feature_importance_rf.png)

## Conclusion
This research validated the development of a stroke prediction model using demographic, lifestyle, and clinical variables. Among all the methods under trial, Random Forest classifier performed the best with ROC AUC >0.80 and PR AUC ~0.30, confirming that the model possesses the capability to rank patients well by relative risk even in a highly imbalanced dataset.

The confusion matrix uncovered the threshold selection trade-offs: at the F1-optimal threshold, 14 cases of stroke were correctly identified but 37 were missed. This underscores a fundamental limit of medical ML — recall maximization is usually preferable over precision maximization where the cost of a false negative (missed stroke) outweighs the cost of a false positive. The calibration curve also indicated that the predicted probabilities were underconfident and that calibration techniques (Platt scaling, isotonic regression) could make outputs more clinically actionable.

Importance analysis upheld clinical wisdom: age, blood pressure, and blood glucose were all good predictors. That this alignment of model-based feature importance with established medical knowledge increases confidence in the technique while raising the question of incorporating in additional weak features (e.g., genetic data, longitudinal history) to make prediction more compelling is intriguing.

Lastly, this paper illustrates how bringing together performance measures (ROC/PR AUC), interpretability measures (feature importance), and diagnostic plots (confusion matrix, calibration curves) provides a model utility assessment.
