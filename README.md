# US Census Income Classification
&
Marketing Segmentation Analysis


## Overview

This project analyzes US Census data (1994-1995) to address two business objectives:

1. **Income Classification:** Predict whether an individual earns above or below $50,000 annually
2. **Population Segmentation:** Identify distinct population segments for targeted marketing and policy development

## Dataset

| Attribute | Value |
|-----------|-------|
| Source | US Census Bureau (Current Population Survey) |
| Records | 199,523 |
| Features | 42 variables (demographic, employment, financial) |
| Years | 1994-1995 |
| Target | Income above/below $50,000 |
| Class Balance | 6.2% high-income / 93.8% low-income |

## Key Results

### Classification

The logistic regression model achieves a weighted AUC of 0.913 using 7 engineered categorical features. Top predictors by odds ratio:

| Feature | Odds Ratio | Interpretation |
|---------|------------|----------------|
| sex_Male | 4.17 | Males 4x more likely to earn high income |
| age_bin_39-55 | 4.12 | Peak earning years |
| age_bin_55-90 | 3.96 | Senior professionals |
| education_level_graduate | 2.24 | Advanced degrees double odds |
| education_level_children | 0.0007 | Children have near-zero odds |

### Population Segmentation

KMeans clustering with k=3 (selected based on business judgment for interpretability) identifies three distinct segments:

| Cluster | Size | Avg Age | Weeks Worked | High Income Rate | Profile |
|---------|------|---------|--------------|------------------|---------|
| 0 | 30.4% | 10 | 0.7 | 0.0% | Children & Dependents |
| 1 | 48.7% | 38 | 45.8 | 11.9% | Active Workforce |
| 2 | 20.9% | 61 | 3.2 | 1.9% | Retirees & Seniors |


## Notebook Contents

1. **Data Loading and Overview** - Load 199,523 records with 42 features
2. **Missing Values Analysis** - Handle placeholders and "Not in universe" responses
3. **Target Variable Distribution** - Examine 6.2% high-income class imbalance
4. **Age Distribution Analysis** - Bimodal distribution with child and adult peaks
5. **Weighted Income Analysis (Demographics)** - Income rates by sex, race, marital status
6. **Weighted Income Analysis (Employment)** - Income rates by education, occupation, industry
7. **Feature Engineering** - Create 6 simplified categorical variables
8. **Information Value Analysis** - Quantify predictive power using WOE/IV
9. **Logistic Regression Model** - Build classifier with AUC 0.913
10. **Population Segmentation** - PCA (5 components) + KMeans (k=3)
11. **Conclusion** - Summary of findings and recommendations

## Feature Engineering

| New Feature | Categories | Source |
|-------------|------------|--------|
| education_level | children, no_diploma, high_school, some_college, bachelors, graduate | education (17 categories) |
| age_bin | 0-12, 12-27, 27-39, 39-55, 55-90 | age (continuous) |
| worker_type | not_in_labor_force, private, government, self_employed, not_working | class of worker |
| marital_group | married_present, married_absent, never_married, divorced_separated, widowed | marital stat |
| citizenship_status | native, naturalized, non_citizen | citizenship |
| has_any_investment | 0, 1 | capital gains, losses, dividends |

## PCA Component Interpretation

| Component | Variance | Interpretation |
|-----------|----------|----------------|
| PC1 | 17.3% | Work intensity (weeks worked, labor force participation) |
| PC2 | 8.3% | Age and life stage (older vs younger, widowed vs never married) |
| PC3 | 7.2% | Race and demographics (White vs Black, citizenship) |
| PC4 | 5.3% | Education and entrepreneurship (graduate, self-employed, investments) |
| PC5 | 5.1% | Education-citizenship contrast (no diploma/non-citizen vs high school/native) |

Total variance explained by 5 components: 43.1%

## Cluster Insights

**Cluster 0 - Children & Dependents (30.4%)**
- Average age 10, nearly zero weeks worked
- 78% have "children" education level, 97% not in labor force
- 100% never married, 0% high income
- Marketing: Family-oriented products, education services

**Cluster 1 - Active Workforce (48.7%)**
- Average age 38, works 46 weeks/year
- 72% private sector, 16% bachelors or graduate degree
- 61% married with spouse present, 12% high income
- Marketing: Financial products, career services, home ownership

**Cluster 2 - Retirees & Seniors (20.9%)**
- Average age 61, only 3 weeks worked/year
- 93% not in labor force, 37% no diploma
- 23% widowed, 62% married, 2% high income
- Marketing: Healthcare, retirement planning, leisure

## Technical Notes

- Survey weights used throughout for population-representative estimates
- "Not in universe" values indicate survey questions that don't apply (e.g., employment questions for children)
- Capital gains/losses capped at 99,999 in original data
- Logistic regression uses L2 regularization with liblinear solver

## Requirements

```
pandas
numpy
matplotlib
seaborn
scikit-learn
```


## Key Findings Summary

- Education is the strongest predictor of income (IV = 6.0)
- Graduate degrees show 50%+ high-income rates vs <1% for no diploma
- Males have 4x higher income rate than females
- Age 39-55 represents peak earning years (15.8% high income)
- Three natural population segments emerge: children, workers, and retirees
- The active workforce segment (Cluster 1) contains nearly all high earners
