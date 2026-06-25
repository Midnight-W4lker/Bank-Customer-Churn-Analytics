# Bank Customer Churn Analytics

## Web Report

A static web representation is available in `docs/index.html`. After enabling GitHub Pages from the `docs` folder, it can be viewed as a project report page.


## Project Overview

This project analyzes customer churn for a bank and builds a predictive workflow for retention planning. The notebook studies which customer attributes are associated with leaving the bank and compares interpretable and nonlinear classification models.

The work is framed around retention action. The goal is not only to predict churn, but to understand which customer groups deserve attention and how a bank could use model thresholds for outreach planning.

## Problem Definition

Banks lose revenue when valuable customers leave. Retention teams need to identify churn risk early enough to act, but outreach has a cost. The challenge is to prioritize customers who are most likely to leave while understanding the business drivers behind that risk.

The key questions are:

- Which customer characteristics are most associated with churn?
- Is churn evenly distributed across geographies, age groups, activity levels, and product counts?
- How should the model handle class imbalance?
- Which threshold should be used when outreach cost changes?
- Which variables are useful for prediction, and which are weaker explanatory signals?

## Dataset

The notebook uses the local CSV:

```text
data/raw/Churn_Modelling.csv
```

The dataset includes customer profile fields, account features, geography, gender, and the target variable `Exited`, where:

- `0` = stayed
- `1` = churned

## What Is Covered

- Data loading from a local CSV
- Data quality and class-balance audit
- Removal of identifier fields
- Descriptive statistics by churn status
- Segment analysis by geography, gender, age band, activity, balance, and product count
- Exploratory visual analytics with count plots, box plots, heatmaps, and model evaluation charts
- Statistical tests for numeric and categorical churn differences
- Correlation and VIF review for multicollinearity
- VADER sentiment applicability audit
- Balanced logistic regression baseline
- Tuned random forest classifier
- Confusion matrix, ROC curve, precision-recall curve, cross-validation, and threshold tradeoff analysis
- Feature importance review for retention planning

## Key Findings

- Churn is imbalanced; most customers stayed, so accuracy alone is not enough.
- Age, activity status, product count, balance behavior, and geography show stronger churn relevance.
- Estimated salary is not a strong churn explanation compared with behavioral and account features.
- Some engineered balance features overlap with original variables, so coefficient-style interpretation requires caution.
- Churn risk varies across customer segments, which makes targeted retention more useful than broad outreach.
- VADER sentiment analysis is not applicable because the dataset does not include complaints, reviews, call notes, or other free text.

## Solution Approach

The solution uses a retention-focused analytics pipeline:

1. Remove identifiers that do not help generalizable prediction.
2. Engineer useful customer behavior indicators such as zero balance, balance-to-salary ratio, and age band.
3. Explore churn patterns across demographics and account behavior.
4. Use statistical tests to identify meaningful differences between churned and retained customers.
5. Train a balanced logistic regression baseline for interpretability.
6. Tune a random forest model to capture nonlinear churn patterns.
7. Evaluate using churn recall, precision, F1, ROC AUC, precision-recall behavior, and threshold planning.

## Results Summary

The tuned churn model provides a practical way to rank customers by churn risk. Feature importance and segment analysis show that customer age, product count, activity status, balance behavior, and geography are more useful than salary alone. Threshold analysis translates predictions into contact strategies.

## Business Solution

The model can support a tiered retention strategy:

- Low risk: monitor only
- Medium risk: low-cost digital outreach
- High risk: direct retention call or targeted offer
- Very high risk: relationship-manager review for valuable customers

The threshold should be selected based on campaign cost. If outreach is cheap, the bank can prioritize recall. If incentives are expensive, precision becomes more important.

## Repository Structure

```text
data/raw/
  Churn_Modelling.csv
notebooks/
  03_customer_churn_prediction.ipynb
outputs/figures/
  Exported charts from the notebook
requirements.txt
README.md
```

## How to Run

```bash
pip install -r requirements.txt
jupyter notebook notebooks/03_customer_churn_prediction.ipynb
```

## Conclusion

Customer churn is best handled as a prioritization problem. The final workflow identifies meaningful churn signals, compares models, and connects predicted risk to retention action rather than treating the model as a standalone prediction exercise.
