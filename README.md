Here is a **simple, normal, clean-English README**.
No heavy academic tone.
No robotic lines.
Just clear writing, like a real project someone would submit.

---

# US Census Income Analysis – README

This notebook explores the 1994–95 US Census dataset to understand which people are more likely to earn above or below $50,000. It includes basic cleaning, feature grouping, income patterns, a logistic regression model, and a final segmentation using PCA and clustering. The goal is to build a clear picture of the population and identify useful groups based on demographics and work behavior.

## What the Notebook Does

* Loads and prepares the dataset
* Handles placeholder values and standardizes categories
* Explores age, education, sex, work activity, and other variables
* Creates simple grouped features such as education levels, worker types, and marital categories
* Calculates Information Value (IV) to see which features matter most
* Builds a weighted logistic regression model
* Performs PCA on selected features
* Runs KMeans to create population segments
* Profiles each segment with averages and category shares

## Main Insights

The data shows a strong skew: only about 6 percent of people earn above $50,000. Age, education, and work weeks play major roles in separating high and low income. Married individuals with steady work and higher education have the highest chances of crossing the income threshold. Groups with limited education, children and teenagers, and people not in the labor force naturally fall on the lower end.

Investment income, although rare, strongly signals higher earnings. Government and self-employed workers perform better than the private and non-working groups. Overall, the analysis highlights clear patterns that match real-world expectations.

## The Model

A simple logistic regression model is trained using demographic and grouped features. Survey weights are used to keep the results population-correct. The model achieves around 0.91 AUC, which shows it separates the classes well despite the imbalance. The strongest positive effects come from males, older working adults (around 40–55), and people with graduate or professional degrees.

## Segmentation

For segmentation, the notebook uses PCA to compress the feature space and KMeans to form clusters. After testing several values, k=7 is selected. These clusters represent meaningful groups, such as children, retired or older groups, working-class adults, mid-income groups, and a high-earning professional segment. This adds an extra layer of understanding to the dataset beyond the supervised model.

## Closing Note

This notebook gives a full pipeline: clean the data, understand the population, build an interpretable model, and create useful segments. It keeps the workflow simple and readable, while offering solid insights that can support reporting, presentations, or further modeling.
