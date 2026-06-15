![Python](https://img.shields.io/badge/Python-3.11-blue)
![MLflow](https://img.shields.io/badge/MLflow-Tracking-blue)
![DagsHub](https://img.shields.io/badge/DagsHub-MLOps-green)
![XGBoost](https://img.shields.io/badge/XGBoost-92%25_Accuracy-orange)
![LightGBM](https://img.shields.io/badge/LightGBM-92%25_Accuracy-brightgreen)

# 🥤 Beverage Price Range Prediction Using Consumer Survey Data

## 📌 Project Overview

This project focuses on predicting a consumer's **Beverage Price Range Preference** (**Budget**, **Mid-Range**, or **Premium**) using demographic and behavioral survey data.

The solution leverages Machine Learning, Feature Engineering, and MLOps practices to build a reproducible and scalable classification pipeline.

---

## 🎯 Business Problem

Beverage companies often struggle to identify which price segment their consumers belong to. Without this information, it becomes difficult to:

* Design effective pricing strategies
* Launch targeted marketing campaigns
* Optimize product placement
* Understand consumer purchasing behavior

This project solves the problem by building a multi-class classification model capable of predicting consumer price preferences based on survey responses.

---

## 📂 Dataset Features

The dataset contains consumer demographic and behavioral information such as:

### Demographic Features

* Age
* Occupation
* Zone
* Income Levels

### Behavioral Features

* Consumption Frequency
* Brand Awareness
* Purchase Channel
* Health Concerns
* Pack Size Preference

### Brand Features

* Current Brand
* Reason for Choosing Brand
* Price Range (Target Variable)

---

## 🛠 Data Preprocessing

### Missing Value Treatment

* Mode Imputation for Consumption Frequency
* "Not Reported" category for missing Income Levels

### Duplicate Removal

* Removed duplicate survey responses

### Outlier Detection

* Applied IQR Method
* Validated using Boxplots

### Data Cleaning

* Corrected inconsistent categorical labels
* Standardized survey responses

### Age Binning

Created age groups:

* Under 25
* 26–35
* 36–45
* 46–55
* 56–70
* Above 70

---

## 🚀 Feature Engineering

### 1️⃣ Consumption Frequency vs Brand Awareness Score

```python
cf_ab_score = consume_frequency / (brand_awareness + 1)
```

Measures brand loyalty and spending potential.

---

### 2️⃣ Zone × Income Score

```python
zas_score = zone_encoded * income_encoded
```

Captures purchasing power based on geographical and income factors.

---

### 3️⃣ Brand Switching Index (BSI)

```python
BSI = 1
```

If consumer:

* Is not loyal to a specific brand
* Chooses products primarily based on Price or Quality

Otherwise:

```python
BSI = 0
```

Identifies consumers likely to switch brands.

---

## 🔄 Encoding Strategy

### Label Encoding

Used for ordinal features:

* Income Levels
* Age Groups

### One-Hot Encoding

Used for nominal categorical variables.

```python
drop_first=True
```

to avoid multicollinearity.

---

## 🤖 Machine Learning Models

The following models were trained and evaluated:

| Model                  | Type              |
| ---------------------- | ----------------- |
| Gaussian Naive Bayes   | Probabilistic     |
| Logistic Regression    | Linear            |
| Support Vector Machine | Kernel-Based      |
| Random Forest          | Ensemble          |
| XGBoost                | Gradient Boosting |
| LightGBM               | Gradient Boosting |

---

## 📊 Evaluation Metrics

### Primary Metric

* Weighted F1 Score

### Secondary Metric

* Accuracy

### Additional Metrics

* Precision
* Recall
* Classification Report

---

## 🏆 Model Performance

| Model               | Accuracy | Weighted F1 Score |
| ------------------- | -------- | ----------------- |
| GaussianNB          | 58%      | 55%               |
| Logistic Regression | 77%      | 77%               |
| SVM                 | 79%      | 79%               |
| Random Forest       | 90%      | 90%               |
| XGBoost             | 92%      | 92%               |
| LightGBM            | 92%      | 92%               |

### Best Performing Models

🥇 LightGBM

🥇 XGBoost

Both achieved approximately **92% Accuracy** and **92% Weighted F1 Score**.

---

## ⚙️ MLOps Implementation

This project incorporates industry-standard experiment tracking using:

### MLflow

Used for:

* Parameter Tracking
* Metric Logging
* Artifact Storage
* Model Comparison

### DagsHub

Used as:

* Remote MLflow Tracking Server
* Experiment Repository
* Collaboration Platform

Each experiment stores:

* Accuracy
* Weighted F1 Score
* Model Parameters
* Classification Reports

---

## 📁 Project Structure

```bash
Beverage-Price-Prediction/
│
│
├── Feature_engg.ipynb
│
└── README.md
```

---

## 📈 Future Improvements

* Hyperparameter Optimization using Optuna
* Model Deployment using FastAPI
* CI/CD Integration
* Dockerization
* Automated Retraining Pipeline
* Real-Time Prediction API

---

## 📸 Project Screenshots

### Model Comparison

[Model Comparison](ssc.png)


### MLflow / DagsHub Tracking

[MLflow Model Tracking](https://dagshub.com/cipherX2433/my-first-repo.mlflow/#/experiments/1/runs?searchFilter=&orderByKey=attributes.start_time&orderByAsc=false&startTime=ALL&lifecycleFilter=Active&modelVersionFilter=All+Runs&datasetsFilter=W10%3D&compareRunsMode=CHART)


## ⭐ If you found this project useful, consider giving it a star!
