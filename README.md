**Patient Readmission Prediction: A Machine Learning Exercise**

**Introduction**

This project is a practical machine learning exercise using Python to explore patient records, train multiple classification models and compare their ability to predict readmission. It covers data preprocessing, exploratory data analysis, feature selection, model development and evaluation.

The intended purpose is to help hospital staff identify patients who may require closer attention after discharge. The exercise investigates whether the supplied data support useful predictions.

**Dataset**

The dataset contains 3,000 patient records and 10 original variables:
- Patient ID
- Age
- Gender
- Admission Type
- Length of Stay
- Number of Diagnoses
- Blood Pressure
- Blood Sugar Levels
- Previous Admissions
- Readmission
Readmission is the target variable, encoded as No = 0 and Yes = 1. Patient ID is excluded from the predictors.

There are 866 readmissions (28.87%) and 2,134 non-readmissions (71.13%). No missing values, duplicate rows or repeated patient IDs were found.

The exercise specifies readmission within 30 days. The dataset contains no dates to verify this interval, so the analysis assumes that the supplied outcome represents this definition.

**Data Preparation and Exploration**

Data preparation included checking data types, standardising text labels, examining missing values and duplicates, and inspecting numeric ranges.

EDA examined outcome balance, numeric distributions by readmission status, and readmission rates by admission type, previous admissions and diagnosis count. A correlation matrix explored linear relationships between variables.

Categorical variables were encoded, and statistical tests supported feature interpretation. Eight predictors were retained for model comparison.

**Model Development**

The following algorithms were trained:
- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting
- Support Vector Classifier
- K-Nearest Neighbours
- Gaussian Naive Bayes
Three additional configurations adjusted logistic regression, decision tree and random forest settings, giving ten configurations in total.

The data were divided into 60% training, 20% validation and 20% test records. Stratification preserved the approximate outcome balance. Standardisation was fitted on training data only.

**Model Evaluation**

Every model was evaluated using:
- Accuracy: Overall correctness.
- Precision: Of predicted readmissions, how many were correct.
- Recall: Of actual readmissions, how many were identified.
- F1-Score: Harmonic mean of precision and recall.
- ROC-AUC: Ability to distinguish between classes.
Classification reports, confusion matrices and ROC curves supported comparison. The best candidate was selected using validation F1, with ROC-AUC used to break ties. Test results were then reported for all models without changing that selection.

**Main Results**

The tuned decision tree achieved the highest validation F1 among the tested configurations. Its test results were:
- Accuracy: 41.5%
- Precision: 27.5%
- Recall: 63.0%
- F1-Score: 0.383
- ROC-AUC: 0.478
It detected 109 of 173 readmissions, missed 64 and produced 287 false alerts.

**Discussion**

An always-No rule achieved 71.2% accuracy while detecting no readmissions. An always-Yes rule achieved an F1 score of 0.448, exceeding the selected model’s F1 while flagging every patient.

These comparisons show why accuracy or F1 alone cannot establish practical usefulness. The selected model detected some readmissions but generated many incorrect alerts and showed weak discrimination.

Feature importance indicated which variables the tree models used most. These rankings do not establish clinical causes or confirmed risk factors.

**Tools Used**

Python, pandas, NumPy, Matplotlib, Seaborn, SciPy and Scikit-learn.

**Learning Outcomes and Limitations**

The exercise developed skills in preprocessing, EDA, multiple-model comparison, class-imbalance assessment and interpretation of prediction errors. It also demonstrated that strong training performance can coexist with weak performance on unseen records.

The evaluation is internal rather than independent external validation. Further work could verify the outcome definition, assess probability calibration and evaluate later hospital records.

**Conclusion**

This project demonstrates a complete machine learning workflow for patient readmission prediction. Although a tuned decision tree was selected, its results did not establish reliable prediction for hospital follow-up prioritisation.

The exercise highlights the importance of comparing models, examining errors and reporting limitations honestly. Full academic references are provided in the notebook.
