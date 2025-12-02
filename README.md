# US Census Income Dataset – Analysis Notebook

This notebook explores the US Census income dataset to understand which demographic and employment factors are linked with earning above or below $50,000. The work includes data cleaning, feature engineering, exploratory analysis, modeling, and segmentation. The goal of the notebook is to build a clear understanding of income patterns and identify meaningful population groups.

## Notebook Flow

The analysis follows these main steps:

### 1. Data Loading and Cleaning

The dataset is loaded with proper column names. Placeholder values such as “Not in universe” and “?” are standardized. Only one column contains true missing values. Most placeholders represent real categories such as children, non-workers, or non-movers.

### 2. Target Distribution

The dataset is highly imbalanced. Only about 6% of individuals fall in the high-income group. This imbalance is important for both interpretation and modeling.

### 3. Exploratory Data Analysis

Age structure, marital status, education, sex, work activity, race, and citizenship are examined. Weighted high-income rates are calculated to reflect the survey design. Clear patterns appear:

* Higher education strongly boosts income.
* Working 40+ weeks is a key factor.
* Married individuals show higher income rates.
* Investment income is a strong signal.
* Males and the 39–55 age group show the highest earnings.

These patterns match the intuition seen in many labor and demographic studies.

### 4. Feature Engineering

Raw categories are grouped into simpler and more useful levels. Education, worker type, marital status, citizenship, and investment indicators are consolidated. This step makes the relationships more visible and reduces noise.

### 5. Information Value (IV)

The strongest predictors are education level, age group, worker type, investment activity, and marital status. These features also match the earlier EDA trends, confirming consistency in the data.

### 6. Logistic Regression Model

A weighted logistic regression model is built using the engineered features. The model achieves an AUC close to 0.91, showing strong predictive ability. Odds ratios show how each feature increases or decreases the likelihood of being in the high-income category.

### 7. PCA and KMeans Segmentation

To understand broader population structure, PCA is applied to reduce the dimensionality, followed by KMeans clustering. Seven distinct clusters appear, including:

* Children and teenagers
* Older adults and retired individuals
* Broad working-class groups
* Mid-income mixed segments
* A high-earning professional and self-employed group

These clusters help summarize the variation in the dataset in a simple way that is easy to interpret.

## Summary

This notebook provides a complete analysis of the US Census income dataset. It cleans and prepares the data, explores important demographic relationships, builds a strong predictive model, and identifies meaningful population segments. The overall results stay consistent across EDA, IV, and modeling, making the findings reliable and clear.

