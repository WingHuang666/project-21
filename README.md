# project-21

# Bedtime Screen Time, Sleep, and Fatigue Analytics Project

## Project Overview

This project investigates the relationships among bedtime behaviors, lifestyle characteristics, sleep outcomes, sleep debt, and next-day fatigue using machine learning and unsupervised learning methods.

The analysis focuses on whether pre-sleep behaviors can help predict different aspects of sleep and fatigue, which variables provide the most useful predictive information, and whether distinct behavioral and sleep profiles can be identified within the dataset.

The project combines regression, multiclass classification, feature importance analysis, and K-Means clustering to examine the dataset from multiple perspectives.

---

## Dataset

The project uses the following dataset:

`bedtime_screentime_sleep_debt.csv`

The dataset contains individual-level information related to demographics, bedtime behavior, lifestyle characteristics, sleep outcomes, and next-day fatigue.

### Main Variables

The dataset includes variables such as:

- Age
- Gender
- Occupation type
- Chronotype
- Bedtime phone minutes
- Primary bedtime app
- Screen brightness percentage
- Blue-light filter usage
- Caffeine consumption after 5 PM
- Physical activity
- Sleep latency
- Total sleep duration
- Deep sleep percentage
- REM sleep percentage
- Morning alarm snoozes
- Next-day fatigue score
- Sleep-debt category

`user_id` is treated as an identifier and is excluded from predictive modeling.

---

## Research Questions

### RQ1 — Sleep Latency Prediction

Can pre-sleep behavior and lifestyle characteristics predict how long it takes an individual to fall asleep?

Multiple regression models are compared, and feature importance is examined to identify the variables that contribute most to sleep-latency prediction.

**Task:** Regression

**Models:**
- Ridge Regression
- Random Forest Regressor
- Extra Trees Regressor

**Primary Evaluation Metric:** MAE

---

### RQ2 — Total Sleep Duration Prediction

Can pre-sleep behavior and lifestyle characteristics predict total sleep duration?

This analysis evaluates whether behavioral and individual characteristics contain sufficient predictive information about how long an individual sleeps.

**Task:** Regression

**Models:**
- Ridge Regression
- Random Forest Regressor
- Extra Trees Regressor

**Primary Evaluation Metric:** MAE

---

### RQ3 — Sleep Debt Classification

Can pre-sleep behavior and lifestyle characteristics classify individuals into different sleep-debt categories?

The target variable contains four ordered sleep-debt categories:

1. Optimal Recovery
2. Mild Deficit
3. Moderate Debt
4. Severe Sleep Debt

Actual sleep outcomes are excluded from the predictors in this analysis to reduce the risk of data leakage.

**Task:** Multiclass Classification

**Models:**
- Logistic Regression
- Random Forest Classifier
- Extra Trees Classifier

**Primary Evaluation Metric:** Macro F1

Additional evaluation includes accuracy, macro precision, macro recall, a classification report, and a confusion matrix.

---

### RQ4 — Next-Day Fatigue Prediction

How much does actual sleep information improve the prediction of next-day fatigue?

Two sets of predictors are compared.

#### Behavioral-Only Model

The first model uses pre-sleep behavior and lifestyle characteristics without actual overnight sleep outcomes.

#### Behavior + Sleep Outcomes Model

The second model expands the predictor set by including sleep-related variables such as:

- Sleep latency
- Total sleep duration
- Deep sleep percentage
- REM sleep percentage
- Morning alarm snoozes

Comparing these two approaches helps evaluate the additional predictive value provided by actual sleep outcomes.

**Task:** Regression

**Models:**
- Ridge Regression
- Random Forest Regressor
- Extra Trees Regressor

**Primary Evaluation Metric:** MAE

---

### RQ5 — Behavioral and Sleep Profiles

Can unsupervised learning identify distinct behavioral and sleep profiles within the dataset?

K-Means clustering is applied to standardized quantitative variables representing bedtime behavior, lifestyle characteristics, sleep outcomes, and fatigue.

Different values of `k` are evaluated using:

- Elbow Method
- Inertia
- Silhouette Score
- Cluster interpretability

The final analysis uses three clusters to provide an interpretable segmentation of behavioral and sleep profiles.

**Task:** Unsupervised Learning

**Model:** K-Means Clustering

**Final Number of Clusters:** `k = 3`

PCA is also used to create a two-dimensional visualization of the discovered clusters.

---

## Data Preprocessing

The project includes preprocessing pipelines for both numerical and categorical variables.

### Numerical Variables

Numerical features are processed using:

- Median imputation
- Standardization when required by the model

### Categorical Variables

Categorical features are processed using:

- Most-frequent-value imputation
- One-hot encoding

The preprocessing steps are incorporated into Scikit-learn pipelines to ensure consistent transformations during model training and evaluation.

---

## Model Evaluation

### Regression

Regression models are evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R²

MAE is used as the primary model-selection metric.

### Classification

Classification models are evaluated using:

- Accuracy
- Macro Precision
- Macro Recall
- Macro F1
- Classification Report
- Confusion Matrix

Macro F1 is used as the primary model-selection metric because it gives equal importance to each sleep-debt category.

### Clustering

K-Means clustering is evaluated using:

- Inertia
- Elbow Method
- Silhouette Score
- Cluster size
- Cluster profile interpretability

---

## Feature Importance

Permutation importance is used to evaluate the contribution of individual predictors to the selected supervised-learning models.

Permutation importance measures how much model performance changes when the values of a feature are randomly shuffled.

This approach allows the project to compare the predictive importance of variables such as bedtime phone use, chronotype, caffeine consumption, sleep duration, and other behavioral or sleep-related characteristics.

Feature importance represents predictive contribution and should not be interpreted as evidence of causation.


---

## Technologies and Libraries

The project is implemented in Python using:

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter / Quarto

