# Diabetes Prediction ML

A machine learning project for early-stage diabetes risk prediction using clinical symptoms and patient information.

## Overview

This project develops and evaluates multiple machine learning classification models for predicting early-stage diabetes based on clinical symptoms.

The following models were evaluated:

- Logistic Regression
- Random Forest
- Support Vector Machine (SVM)
- XGBoost

The models were evaluated using stratified 5-fold cross-validation and an independent test set.

## Dataset

Dataset: UCI Early Stage Diabetes Risk Prediction Dataset

The dataset contains patient demographic information and clinical symptoms related to early-stage diabetes.

### Data preprocessing

The following preprocessing steps were performed:

- Duplicate removal
- Train-test split using stratification
- One-hot encoding of categorical features
- Feature scaling for SVM
- Prevention of data leakage using Scikit-learn Pipelines

After removing duplicate records, the dataset contained 251 samples.

## Experimental Setup

### Train-Test Split

- Training set: 80%
- Test set: 20%
- Random state: 42
- Stratified splitting

### Cross-Validation

Stratified 5-fold cross-validation was used on the training set.

## Hyperparameter Tuning

GridSearchCV was used to optimize the SVM hyperparameters.

Best parameters:

```text
C = 1
gamma = scale
kernel = RBF

## Model Comparison

| Model | Accuracy | Precision | Recall | F1 | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 88.50% | 92.75% | 90.56% | 91.49% | 96.86% |
| Random Forest | 94.00% | 95.75% | 95.66% | 95.65% | 97.72% |
| **SVM** | **94.50%** | **95.71%** | **96.40%** | **96.04%** | **98.13%** |
| XGBoost | 92.50% | 94.94% | 94.23% | 94.51% | 97.56% |

SVM achieved the strongest overall cross-validation performance.
Final Test Performance
The selected SVM model was evaluated on the untouched test set.
Metric	Score
Accuracy	92.16%
Precision	96.97%
Recall	91.43%
F1-score	94.12%
ROC-AUC	96.61%
PR-AUC	98.70%


Confusion Matrix
                 Predicted
                 Negative  Positive

Actual Negative      15        1
Actual Positive       3       32

Threshold Analysis
The default threshold of 0.5 provided the highest F1-score among the tested thresholds.
At threshold 0.5:
- Precision: 96.97%
- Recall: 91.43%
- F1-score: 94.12%
A lower threshold of 0.3 increased recall to 94.29%, demonstrating the trade-off between precision and recall.
Project Structure
Diabetes_prediction_ml/
├── diabetes_prediction_ml.ipynb
├── final_svm_model.pkl
├── model_comparison_cv.csv
└── final_svm_test_results.csv

Technologies
- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- Matplotlib
- Google Colab
- Jupyter Notebook
Limitations
- The dataset is relatively small.
- The evaluation is based on a single dataset.
- External validation on an independent dataset was not performed.
- The model should not be considered a clinical diagnostic tool.
Future Work
Potential future improvements include:
- External validation using larger datasets
- Testing additional machine learning models
- Feature selection and optimization
- Evaluation on more diverse patient populations
- Prospective clinical validation
Disclaimer
This project is developed for educational and research purposes. The predictions should not be used as a substitute for professional medical diagnosis.
