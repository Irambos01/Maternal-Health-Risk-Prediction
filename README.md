# Maternal-Health-Risk-Prediction

Project Summary

This project focuses on building a machine learning model to accurately classify pregnant patients into specific risk categories based on clinical and demographic data. The primary objective was to prioritize Recall for the most critical classes: High Risk and EAR (Early Adolescence Risk), ensuring that fewer high-risk cases are missed (minimizing false negatives).

The analysis involved extensive feature engineering to improve predictive power, rigorous comparison between two leading ensemble models (Random Forest and Extreme Gradient Boosting), and validation of feature importance.

1. Data and Target Classes

Dataset: Maternal_Dataset _Updated.csv

Target Variable: Risk Level (Multi-class classification)

Critical Classes: Due to the severe consequences of missing a true positive, the models were evaluated primarily on the Recall of the High and EAR classes.

2. Feature Engineering

The following features were created and used to replace the original, less-predictive columns (Age, Systolic BP, Diastolic):

Engineered Feature



1. Age_Bins: Categorical features representing age ranges (e.g., Age_48+, Age_38-42).

Captures non-linear risk increases associated with specific age groups.

2. MAP: Mean Arterial Pressure, calculated from Systolic and Diastolic BP.

Provides a single, clinically relevant metric for overall blood pressure load.

3. Hypertensive_Flag: Binary flag set to 1 if BP is at or above $140/90$.

Binarizes the immediate risk of clinical hypertension.

4. Overweight_Diabetic_Risk: Interaction term set to 1 if a patient is Overweight (BMI $\ge$ 25) AND has Any Diabetes (Preexisting or Gestational).

Captures the synergistic risk of combined metabolic issues.


Model Selection and Rationale

Two powerful ensemble methods were trained and compared: Random Forest Classifier (RF) and Gradient Boosting Classifier (GB).


<img width="875" height="94" alt="image" src="https://github.com/user-attachments/assets/1f3c0729-5468-40d3-b056-6e966b44cb5b" />


Final Selection: Gradient Boosting Classifier

The Gradient Boosting Classifier was selected because of its significantly superior performance on the most critical metric:

Superior EAR Recall: At {0.86}, the GB model successfully identifies 12% percentage points more of the actual Early Adolescence Risk (EAR) cases compared to the RF model (0.74). This minimizes the risk of missing a critical early-risk patient, aligning perfectly with the project's goal.

4. Final Feature Importance (Random Forest and Gradient Boosting)

Before any feature was engineered, The Age variable was the most predictor(taking 50%, as compared to other predictors). The Feature engineering was done with the aim to distribute the predictive power, to most clinically-relevant factors such as blood sugar, Heart rate, Previous complications,...

The model's predictions are primarily driven by these high-impact features:
1. Feature Importance for Random Forest
   
<img width="989" height="590" alt="Untitled" src="https://github.com/user-attachments/assets/1b60d17b-534b-472c-87b9-08fb469889f2" />

2. Feature importance for XGBoost
   

<img width="989" height="590" alt="Untitled" src="https://github.com/user-attachments/assets/fc8ac725-3343-4b95-99ce-d1ffc97c33ac" />

The importance scores confirm that the models takes into account the clinical factors to be the highest predictors.(Blood Sugar, Heart rate, BMI). Also the early adolescence Risk group (Age_12_17), remains top predictor. 
