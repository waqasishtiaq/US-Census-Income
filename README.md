# US Census Income Classification and Population Segmentation

Predicting income levels and segmenting the US population using 1994-1995 Census Bureau data.

## Overview

This project analyzes US Census data to accomplish two objectives:

1. **Income Classification:** Build a model to predict whether an individual earns above or below $50,000 annually based on demographic and employment characteristics.

2. **Population Segmentation:** Use unsupervised learning (PCA + KMeans) to identify distinct population segments for marketing and policy applications.

The dataset contains 199,523 records with 42 variables covering demographics, education, employment, and financial information.

## Key Results

**Classification Model:**
- Weighted logistic regression achieves AUC of 0.91 on test data
- Strongest predictors: education level (IV=6.00), age group (IV=4.83), worker type (IV=1.25)
- Males have 4.2x higher odds of high income than females
- Graduate education increases odds by 2.2x

**Population Segmentation:**
- 7 distinct clusters identified using KMeans on 5 PCA components
- Segments range from children (Cluster 0, 6) to high earners (Cluster 5 with 29% high income rate)
- Silhouette score of 0.46 indicates reasonable cluster separation

## Dataset

| Attribute | Value |
|-----------|-------|
| Source | US Census Bureau (1994-1995 CPS) |
| Records | 199,523 |
| Variables | 42 |
| Target | Income above/below $50,000 |
| Class Balance | 6.2% high income, 93.8% low income |

## Project Structure

```
census-income-analysis/
    census-bureau.csv              <- Raw data file
    01_final_eda.ipynb             <- Complete analysis notebook
    README.md                      <- This file
```

## Notebook Contents

1. **Data Loading and Overview**
2. **Missing Values and Placeholder Analysis**
3. **Target Variable Distribution**
4. **Age Distribution Analysis**
5. **Weighted Income Analysis by Demographics**
6. **Weighted Income Analysis by Employment**
7. **Feature Engineering**
   - Judgment-based binning (education_level, age_bin, worker_type, marital_group, citizenship_status)
   - Investment income indicators
8. **Information Value Analysis (WOE and IV)**
9. **Logistic Regression Model**
10. **Population Segmentation with PCA and KMeans**
    - Feature scaling
    - PCA exploration and component interpretation
    - KMeans cluster selection (elbow and silhouette)
    - Cluster profiles and interpretation
11. **Conclusion**

## Feature Engineering

Six engineered features were created using judgment-based binning:

| Feature | Categories | Notes |
|---------|------------|-------|
| education_level | 6 levels | Collapsed from 17 original categories |
| age_bin | 5 groups | 0-12, 12-27, 27-39, 39-55, 55-90 |
| worker_type | 5 types | not_in_labor_force, private, government, self_employed, not_working |
| marital_group | 5 groups | married_present, married_absent, never_married, divorced_separated, widowed |
| citizenship_status | 3 groups | native, naturalized, non_citizen |
| has_any_investment | Binary | Any capital gains, losses, or dividends |

## Cluster Profiles Summary

| Cluster | Size | Avg Age | Weeks Worked | High Income Rate | Profile |
|---------|------|---------|--------------|------------------|---------|
| 0 | 23.4% | 9 | 0.7 | 0.0% | Children/Dependents |
| 1 | 17.2% | 63 | 2.5 | 1.5% | Retirees/Seniors |
| 2 | 33.3% | 37 | 45.5 | 8.9% | Core Workers |
| 3 | 4.8% | 37 | 23.8 | 2.5% | Mixed/Transitional |
| 4 | 6.1% | 40 | 38.7 | 5.7% | Mid-Career Workers |
| 5 | 8.8% | 46 | 44.3 | 28.6% | High Earners/Professionals |
| 6 | 6.4% | 13 | 0.4 | 0.0% | Teenagers/Young Dependents |

## Technical Notes

**Survey Weights:** All income rate calculations use survey weights to produce population-representative estimates.

**Placeholder Values:** "Not in universe" and "?" values were standardized to "Not_applicable" as they represent valid survey responses for non-applicable questions.

**PCA Components:** 5 components explain 43% of variance. Key interpretations:
- PC1: Work intensity and labor force status
- PC2: Age and life stage
- PC3: Race and demographics
- PC4: Education, self-employment, and investment
- PC5: Education and citizenship contrast

## Requirements

```
pandas
numpy
matplotlib
seaborn
scikit-learn
```



