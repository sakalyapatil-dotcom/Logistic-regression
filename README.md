Framingham 10-Year Coronary Heart Disease Prediction

This project uses Logistic Regression to predict whether a person is likely to develop coronary heart disease (CHD) within 10 years using the Framingham dataset.

Files

logisticreg.ipynb — Jupyter Notebook containing the complete data preparation, model training, prediction, and cross-validation workflow.

framingham(1).csv — Framingham dataset used by the notebook.

Dataset

The dataset contains 4,238 rows and 16 columns.

Target

TenYearCHD — whether the person developed coronary heart disease within 10 years.

0 = No

1 = Yes

Features

Column

Description

male

Gender indicator

age

Age

education

Education level

currentSmoker

Current smoking status

cigsPerDay

Cigarettes smoked per day

BPMeds

Whether the person takes blood-pressure medication

prevalentStroke

Previous stroke indicator

prevalentHyp

Hypertension indicator

diabetes

Diabetes indicator

totChol

Total cholesterol

sysBP

Systolic blood pressure

diaBP

Diastolic blood pressure

BMI

Body Mass Index

heartRate

Heart rate

glucose

Glucose level

TenYearCHD

Target variable

Workflow

The notebook follows these main steps:

Load NumPy, Pandas, and Matplotlib.

Load the Framingham CSV dataset.

Inspect the dataset using head().

Calculate the percentage of missing values in each column.

Remove rows containing missing values in these selected columns:

education

cigsPerDay

totChol

BMI

heartRate

BPMeds

Check missing values again.

Check for duplicate rows.

Separate features (X) and target (y).

Split the data into training and testing sets using an 80/20 split.

Standardize the features using StandardScaler.

Fill remaining missing values using SimpleImputer(strategy="mean").

Train a LogisticRegression model.

Generate predictions on the test set.

Evaluate the model using recall.

Perform 5-fold cross-validation using recall as the scoring metric.

Model

The project uses:

LogisticRegression()

Logistic Regression is a classification algorithm used here because TenYearCHD is a binary target.

Evaluation

The notebook focuses on recall:

cross_val_score(
    model,
    X_train,
    y_train,
    cv=5,
    scoring="recall"
).mean()

The recorded mean 5-fold cross-validation recall in the notebook is approximately:

0.0708

Recall measures how many of the actual positive cases are correctly identified by the model.

Libraries Used

NumPy

Pandas

Matplotlib

Scikit-learn

How to Run

Place logisticreg.ipynb and framingham(1).csv in the appropriate directory.

Open the notebook in Jupyter Notebook, JupyterLab, or Google Colab.

Update the CSV path if necessary:

df = pd.read_csv("framingham(1).csv")

Run the notebook cells from top to bottom.

Project Goal

The goal of this project is to practice a complete beginner-level machine-learning classification workflow:

Data loading → Missing-value handling → Train/Test Split → Scaling → Logistic Regression → Prediction → Recall → Cross-validation

Note

This is an educational machine-learning project and should not be used as a medical diagnostic system.
