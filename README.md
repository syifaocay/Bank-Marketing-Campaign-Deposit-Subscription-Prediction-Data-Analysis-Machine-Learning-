# Bank Marketing Campaign - Deposit Subscription Prediction

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Scikit--learn](https://img.shields.io/badge/scikit--learn-FF6F00?style=for-the-badge&logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-59B36B?style=for-the-badge&logo=xgboost&logoColor=white)
![LightGBM](https://img.shields.io/badge/LightGBM-4A4A4A?style=for-the-badge&logo=lightgbm&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)

**Data-Driven Campaign Strategy Optimization for Term Deposit Marketing**

---

## 📋 Table of Contents
- [Project Overview](#project-overview)
- [Business Problem & Objectives](#business-problem--objectives)
- [Dataset Description](#dataset-description)
- [Key Insights](#key-insights)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Methodology](#methodology)
- [Feature Engineering & Selection](#feature-engineering--selection)
- [Modeling Pipeline](#modeling-pipeline)
- [Hyperparameter Tuning](#hyperparameter-tuning)
- [Results & Model Comparison](#results--model-comparison)
- [Business Impact](#business-impact)
- [Project Structure](#project-structure)
- [Technologies Used](#technologies-used)
- [How to Reproduce](#how-to-reproduce)
- [Contributors](#contributors)
- [License](#license)

---

## 🎯 Project Overview

This end-to-end data science project focuses on **optimizing direct marketing campaigns** for term deposits in a Portuguese banking institution. By applying advanced machine learning techniques, we developed a predictive model that significantly improves targeting accuracy and campaign efficiency.

The project demonstrates strong capabilities in handling **imbalanced classification problems**, feature engineering, model benchmarking, and business-oriented evaluation metrics.

**Final Best Model**: XGBoost + Neighbourhood Cleaning Rule (NCR)  
**Best F1-Score**: **51.29%** (after hyperparameter tuning)

---

## 💼 Business Problem & Objectives

### Background
Despite extensive telemarketing efforts, the bank only achieved an **11.3% success rate** (4,640 successful subscriptions out of 41,188 contacts). This resulted in high operational costs and suboptimal ROI.

### Key Business Questions
- Which customer segments have the highest probability of subscribing?
- How can we reduce unnecessary calls while maintaining or increasing conversions?
- What is the optimal combination of campaign timing, customer profile, and contact strategy?

### Project Objectives
1. Perform comprehensive EDA and identify key success drivers
2. Build robust classification models with focus on **Precision-Recall trade-off**
3. Handle severe class imbalance using multiple resampling strategies
4. Conduct rigorous model benchmarking and hyperparameter optimization
5. Deliver actionable insights and quantify business impact

---

## 🔍 Key Insights

- **Duration** of the call is the strongest single predictor — longer calls are strongly associated with higher subscription probability.
- Customers with **previous successful campaign outcome** (`poutcome = success`) have dramatically higher conversion rates.
- **Economic context matters**: Lower `euribor3m` and employment variation rate correlate with higher subscription likelihood.
- **Demographic sweet spots**: Students, retired individuals, and customers with university degrees show significantly higher response rates.
- **Age pattern**: Middle-aged customers (30-60) are more responsive compared to very young or very senior groups, though retired seniors remain a high-value segment.
- **Contact efficiency**: Success rate drops significantly after the 3rd contact attempt — further calls yield diminishing returns.
- **Seasonality**: Campaigns in March, April, and December tend to perform better than other months.
- **Feature importance**: Macroeconomic indicators and campaign history features contribute more than some basic demographic variables (e.g., `loan` and `housing` were safely removed during selection).

---

## 📊 Exploratory Data Analysis

Key insights from EDA include strong correlation between `duration` and subscription success, influence of economic indicators, and clear class imbalance problem requiring specialized handling.

*(Detailed visualizations available in the Jupyter Notebook)*

---

## 🛠️ Methodology

### 1. Data Preparation
- Data cleaning and type conversion
- Outlier analysis
- Stratified train-test split (80:20)

### 2. Feature Engineering & Selection
- Created `age_group` feature
- Ordinal encoding for `education`
- One-hot encoding for nominal categorical variables
- **Feature Selection** using Pearson Correlation and Chi-Square Test
- Removed low-importance features: `nr.employed`, `emp.var.rate`, `loan`, `housing`

### 3. Preprocessing Pipeline
- StandardScaler for distance-based models
- No scaling for tree-based models
- ColumnTransformer for streamlined preprocessing

### 4. Imbalance Handling
Tested 6 techniques including **Neighbourhood Cleaning Rule (NCR)** as the most effective.

---

## 🤖 Modeling Pipeline

**Algorithms Benchmarked**: Logistic Regression, KNN, Random Forest, XGBoost, LightGBM.

**Evaluation Strategy**: 5-Fold Stratified Cross-Validation with focus on **F1-Score** and **PR-AUC**.

---

## ⚙️ Hyperparameter Tuning

Extensive GridSearchCV was performed on the best pipeline.

**Final Performance (Test Set)**:

| Metric       | Before Tuning | After Tuning | Improvement |
|--------------|---------------|--------------|-------------|
| **F1-Score** | 49.89%        | **51.29%**   | **+1.40%**  |
| **PR-AUC**   | 46.21%        | **46.68%**   | +0.47%      |
| **Recall**   | 49.14%        | 50.32%       | +1.18%      |
| **Precision**| 50.67%        | 51.60%       | +0.93%      |

---

## 💰 Business Impact

- **Cost Reduction**: Potential **88.9%** reduction in telemarketing operational costs
- **Improved Targeting**: Better balance between cost efficiency and opportunity capture
- **Strategic Recommendation**: Focus marketing efforts on customers with prior success, favorable economic conditions, and high-potential demographic segments.
