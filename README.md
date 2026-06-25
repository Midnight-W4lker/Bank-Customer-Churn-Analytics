---
noteId: "1316ac40709f11f19ec49d9bd6d884a1"
tags: []

---

# Customer Churn Prediction and Retention Analytics

This repository contains a completed analytics notebook for studying customer churn in a bank dataset. The notebook is written as a retention-focused research report rather than a simple model demo.

## What This Notebook Covers

- Dataset loading from a local CSV
- Data quality and class-balance audit
- Descriptive statistics by churn status
- Segment analysis by geography, gender, age band, activity, and product count
- Exploratory visual analytics with box plots, heatmaps, count plots, and model evaluation charts
- Statistical tests for numeric and categorical churn differences
- Correlation and VIF review for multicollinearity
- VADER sentiment applicability audit
- Balanced logistic regression baseline
- Tuned random forest classifier
- Confusion matrix, ROC curve, precision-recall curve, cross-validation, and threshold tradeoff analysis
- Feature importance review for retention planning

## Main Result

Age, activity status, product count, balance behavior, and geography provide stronger churn signal than estimated salary. Because churners are the minority class, model quality is evaluated with recall, precision, F1, ROC AUC, precision-recall behavior, and threshold tradeoffs rather than accuracy alone.

## How to Run

```bash
pip install -r requirements.txt
jupyter notebook notebooks/03_customer_churn_prediction.ipynb
```

The notebook expects this file:

```text
data/raw/Churn_Modelling.csv
```

Exported charts are saved in `outputs/figures/`.
