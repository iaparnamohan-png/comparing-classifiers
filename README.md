# Goal
The goal is to compare the performance of the classifiers (k-nearest neighbors, logistic regression, decision trees, and support vector machines) - Comparing classifiers on bank marketing data 
## Overview
This project compares four classification models on a bank marketing dataset to predict whether a customer will subscribe to a term deposit. The models compared are Logistic Regression, Decision Tree, KNN, and SVM.

## Business Problem
A Portuguese bank runs phone-based marketing campaigns to get customers to subscribe to a term deposit. The dataset has a significant class imbalance — ~89% of customers did not subscribe. The goal is to build a model that identifies which customers are most likely to subscribe, so the bank can focus its outreach and reduce wasted calls.

## Dataset
- **Source:** UCI Machine Learning Repository — Bank Marketing Dataset
- **Link:** https://archive.ics.uci.edu/dataset/222/bank+marketing
- **Size:** 41,188 rows, 20 features
- **Target:** y — did the customer subscribe? (yes/no)
- **Class imbalance:** ~89% No, ~11% Yes

## Key Findings

### Default Model Performance
| Model | Train Time (s) | Train Accuracy | Test Accuracy |
|---|---|---|---|
| Logistic Regression | 0.2592 | 0.8875 | 0.8874 |
| Decision Tree | 0.0002 | 0.9171 | 0.8932 |
| KNN | 0.0534 | 0.9003 | 0.8796 |
| SVM | 16.9032 | 0.8876 | 0.8875 |

### Tuned Model Performance (F1 Score)
| Model | Test Accuracy | F1 Score |
|---|---|---|
| Logistic Regression | 0.5848 | 0.2532 |
| Decision Tree | 0.6946 | 0.3092 |
| KNN (tuned) | 0.6357 | 0.1478 |
| SVM (tuned) | 0.6247 | 0.2380 |

### Why F1 Score?
Accuracy alone is misleading with imbalanced data. A model predicting "no" every time achieves ~89% accuracy but catches zero subscribers. F1 score balances precision and recall and penalizes models that miss actual subscribers — which is the most costly error for the bank.

### Recommended Model: Decision Tree
Decision Tree came out on top with the highest F1 score (0.31) after tuning, and is the fastest model to train. It's also fully interpretable — the bank's marketing team can trace exactly which customer attributes drive subscription likelihood and act on those insights directly.

## Actionable Insights
1. **Default status matters most** — customers with unknown default status are less likely to subscribe. The bank should prioritize customers with a clean credit profile
2. **Job type is a strong signal** — retired and student customers are more likely to subscribe; blue-collar and entrepreneur segments are less likely
3. **Marital status plays a role** — single customers show a higher likelihood of subscribing
4. **Age is predictive** — older customers tend to show higher subscription rates
5. Use the model to score all customers before each campaign and focus calls on the top-ranked segment to improve ROI without adding more calls

## Next Steps
1. Expand features to include campaign and socioeconomic variables (columns 8-20) to improve F1 further
2. Deploy the model as a pre-call scoring tool — rank customers by predicted probability before each campaign
3. Retrain the model as new campaign data comes in
4. A/B test a model-guided team vs a control group to measure real-world impact
