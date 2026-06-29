# Bank Marketing Campaign - Deposit Subscription Prediction

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-FF6F00?style=for-the-badge&logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-59B36B?style=for-the-badge&logo=xgboost&logoColor=white)
![LightGBM](https://img.shields.io/badge/LightGBM-4A4A4A?style=for-the-badge)

**Data-Driven Campaign Strategy Optimization for Term Deposit Marketing**

---

## 📋 Table of Contents
- [Project Overview](#project-overview)
- [Business Problem](#business-problem)
- [Dataset](#dataset)
- [Objectives](#objectives)
- [Methodology](#methodology)
- [Key Features & Preprocessing](#key-features--preprocessing)
- [Modeling & Evaluation](#modeling--evaluation)
- [Results](#results)
- [Project Structure](#project-structure)
- [How to Run](#how-to-run)
- [Contributors](#contributors)
- [Acknowledgments](#acknowledgments)

---

## 🎯 Project Overview

This project aims to **optimize the effectiveness of a bank's term deposit marketing campaign** by leveraging predictive analytics and machine learning. Using historical telemarketing data from a Portuguese bank, we built a robust model capable of predicting which customers are most likely to subscribe to a term deposit.

The solution helps the bank **significantly reduce operational costs** while **increasing conversion rates** by focusing marketing efforts on high-potential customers.

---

## 💼 Business Problem

In the banking industry, direct marketing campaigns (especially via phone calls) are costly and often have low conversion rates. In this dataset, the baseline success rate was only **11.3%** (4,640 successful subscriptions out of 41,188 contacts).

**Main Challenges:**
- High cost per call with low ROI
- Difficulty identifying high-potential customers
- Imbalanced target variable (heavily skewed toward "No")

**Goal:** Build a predictive model that can:
- Identify customers with high subscription probability
- Improve campaign efficiency
- Reduce unnecessary calls (potential cost reduction up to **88.9%**)

---

## 📊 Dataset

- **Source**: [UCI Machine Learning Repository - Bank Marketing Dataset](https://archive.ics.uci.edu/dataset/222/bank+marketing)
- **Creator**: Sérgio Moro, Paulo Cortez, Paulo Rita (2014)
- **Period**: May 2008 - November 2010
- **Total Records**: 41,188
- **Target Variable**: `y` (Yes = client subscribed to term deposit)

**Key Feature Groups:**
- **Demographic**: `age`, `job`, `marital`, `education`
- **Financial**: `default`, `housing`, `loan`, `balance`
- **Campaign**: `contact`, `month`, `day_of_week`, `duration`, `campaign`, `previous`, `poutcome`
- **Economic Context**: `emp.var.rate`, `cons.price.idx`, `cons.conf.idx`, `euribor3m`, `nr.employed`

---

## 🚀 Objectives

1. Understand customer characteristics that influence term deposit subscription
2. Build high-performance classification models with focus on **F1-Score**, **PR-AUC**, **Recall**, and **Precision**
3. Handle class imbalance using various resampling techniques
4. Optimize model through hyperparameter tuning
5. Provide actionable insights for marketing strategy optimization

---

## 🔧 Methodology

### 1. Data Preparation
- Exploratory Data Analysis (EDA)
- Handling missing values and outliers
- Feature engineering (Age groups, etc.)

### 2. Preprocessing
- **Scaling**: StandardScaler (for distance-based models)
- **Encoding**: One-Hot Encoding + Ordinal Encoding
- **Feature Selection**: Pearson Correlation + Chi-Square Test

### 3. Modeling
- **Benchmarked Algorithms**:
  - Logistic Regression
  - KNN
  - Random Forest
  - XGBoost
  - LightGBM
- **Imbalance Handling**:
  - RandomOverSampler, SMOTE, ADASYN, NearMiss, TomekLinks, **Neighbourhood Cleaning Rule (NCR)**

### 4. Evaluation
- 5-Fold Stratified Cross Validation
- Primary Metric: **F1-Score**
- Additional: PR-AUC, Recall, Precision

---

## 🏆 Results

**Best Model**: **XGBoost + Neighbourhood Cleaning Rule (NCR)**

| Metric       | Before Tuning | After Tuning | Improvement |
|--------------|---------------|--------------|-------------|
| **F1-Score** | 49.89%        | **51.29%**   | +1.40%      |
| **PR-AUC**   | 46.21%        | **46.68%**   | +0.47%      |
| **Recall**   | 49.14%        | **50.32%**   | +1.18%      |
| **Precision**| 50.67%        | **51.60%**   | +0.93%      |

**Business Impact**:
- Significant improvement in campaign efficiency
- Potential **88.9% reduction** in telemarketing operational costs
- Better balance between cost efficiency (Precision) and opportunity capture (Recall)

---
