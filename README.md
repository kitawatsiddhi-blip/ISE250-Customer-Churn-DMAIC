# Customer Churn Prediction & Reduction — Six Sigma DMAIC + Machine Learning

**SJSU ISE 250 — Leading Six Sigma Improvement | Final Project**
Team project (5 members) · Prof. Dr. Behin Elahi

---

## Problem

Telecom has the highest churn of any major sector, and losing a customer costs
6–7x more than keeping one. Working from the IBM Telco dataset (5,043 customers,
25 variables), we treated a cancellation as a **process defect** and ran the full
Six Sigma DMAIC cycle — so the statistics and the machine learning both feed one
business decision instead of sitting in separate silos.

## DMAIC

**Define** — Baseline churn of **26.5%** (1,336 of 5,043 customers lost).
Translated to Six Sigma terms: **264,922 DPMO, sigma level 2.12**. Goal set at
under 10% churn. Scoped with a SIPOC diagram and project charter.

**Measure** — Established the baseline metrics and built a CTQ tree. Churned
customers averaged **$75.21/month vs $67.84** for retained, and had far shorter
tenure (**18.2 vs 37.6 months**).

**Analyze** — EDA, correlation, and binary logistic regression in Minitab.
Chi-square tests significant at **p = 0.000**. Root causes ranked with fishbone
and Pareto analysis:

| Driver | Churn rate |
|---|---|
| First 12 months of tenure | **50.3%** (vs 10% at 49+ months) |
| Electronic check payment | **44.3%** (vs 17.4% bank transfer) |
| Month-to-month contract | **43.8%** (vs 4.0% two-year) |
| No tech support | **41.1%** (vs 8.6% with support) |
| Fiber optic service | **42.1%** (vs 19.5% DSL) |

**Improve** — Four data-backed interventions, each tied to a confirmed root cause:
contract upgrade incentive, structured onboarding at months 3/6/9, auto-pay
migration credit, and bundled tech support on fiber plans. Projected impact:
churn **26.5% → ~10%**, sigma **2.12 → 2.78**, roughly **$62,552/month** in
retained revenue.

**Control** — Monthly P-chart monitoring in Minitab (UCL 0.32) across five KPIs,
with a three-level escalation plan if churn trends back up.

## Machine Learning

| Model | Test Accuracy | AUC |
|---|---|---|
| **Logistic Regression** | **77.0%** | **0.83** |
| Random Forest | 76.5% | 0.82 |
| Decision Tree | 69.4% | 0.63 |

Logistic Regression was selected. The Decision Tree hit **100% training accuracy
against 69.4% on test** — a textbook overfit, and the reason it was rejected
despite looking strongest on paper.

Deployment concept: score all active customers monthly, flag anyone above 70%
churn probability, route to the retention team.

**Honest limitation:** recall on the churn class is only ~45%. The model is better
at confirming who will stay than catching everyone who will leave. Class balancing
(SMOTE) is the obvious next step.

## Files

| File | Contents |
|---|---|
| `python.ipynb` | Cleaning, EDA, model training and evaluation |
| `Minitab_Analysis.mpx` | Logistic regression, chi-square, control charts |
| `Customer Churn-ISE250.pptx` | Final presentation |

## Tools

Python (pandas, scikit-learn, matplotlib) · Minitab · Six Sigma DMAIC
