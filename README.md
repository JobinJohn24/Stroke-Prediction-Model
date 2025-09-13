# Stroke Prediction Model
A machine learning project to predict stroke risk using clinical and lifestyle features. This repository walks though the complete workflow: data analysis, preprocessing, model training, evaluation interpretability, and calibration

# Introduction
Stroke is the leading cause of mortaility and disbaility. early risk detection can enable preventive healthcare intervention and reduce long-term burden. This project builds predictive models on a public healthcare dataset to classify patients as at risk of stroke (stroke = 1) or not (stroke = 0).

Data Overview

1.1 
Dataset: 

1.2 Target distribution
* Stroke = 1 (positive): 10%
* Stroke = 0 (negative): 90%

![Target Distribution](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/target_distribution.png)

1.3 Features 
* Numeric features: age, average glucose level, BMI
* Categorical features: gender, residence type, work type, marital status, smoking status
* ![Histogram: average_glucose_level](https://github.com/JobinJohn24/Stroke-Prediction-Model/blob/main/histogram_avg_glucose_level.png)

# Metholody
2.1 Preprocessing
* Numeric features: Missing values were imputed using the median, the features were standarized to make sure models such as Logistic Regression weren't numerical biased on scale differences ie glucose vs age
* Categorical features: Missing values were imputed with the most common category, then turned into a one-hot encoding (y/n) so the model training and splitting would be efficent.
* Imbalance handling: The dataset established a precedent of 1 in 10 patients actually having/had a stroke, the dataset was skewed to account for the "no stroke." To fix the issue, class weights (modifying the models loss function to account for a larger penalty comparitive to the errors on the non-stroke cases) and SMOTE (Synthetic Minority Over Sampling Technique - generating minority samples and interpolating between existing ones in feature space) techniques were used.
