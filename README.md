# CMS Hospital Readmission Risk Analysis

A complete end-to-end healthcare analytics solution using CMS hospital 
readmissions data — applying Python for data cleansing and predictive 
modelling, and delivering an interactive Power BI dashboard presenting 
30-day readmission risk stratification, patient cohort trends, and cost 
impact indicators to support clinical decision-making.

---

## Project Overview

| Item | Detail |
|------|--------|
| Dataset | 5,000 CMS-style patient encounters |
| Period | Jan 2023 – Feb 2024 |
| Hospitals | 6 facilities |
| Diagnoses | 10 CMS conditions |
| Champion model | Gradient Boosting (GBM) |
| Model AUC-ROC | 0.627 |
| Readmission rate | 64.3% |
| Critical risk patients | 3,017 (60.3%) |
| Total dataset cost | $147.9M |

---

## Project Structure
cms-readmission-risk-analysis/
* Notebook_01_Data_Collection.ipynb
* Notebook_02_Data_Cleansing.ipynb
* Notebook_03_Feature_Engineering.ipynb
* Notebook_04_Modelling.ipynb
* CMS_Readmission_Dashboard.pbix
* requirements.txt
* cms_patients_raw.csv
* fact_patients_scored.csv
* agg_monthly_kpis.csv
* agg_diagnosis.csv
* agg_hospital.csv
* agg_risk_tiers.csv
* patient_watchlist.csv
* feature_importance.csv
* dim_date.csv
* cleansing_report.json
* model_performance.json

---

## Pipeline Steps

### Step 1 — Data Collection
Generates a realistic 5,000-record CMS-style inpatient dataset with
clinically grounded distributions. Injects 5% dirty records to
demonstrate the cleansing step.

### Step 2 — Data Cleansing
Applies 15 data quality rules across five severity levels:

| Rule | Issue | Severity |
|------|-------|----------|
| R01 | Duplicate patient IDs | CRITICAL |
| R02 | Age outside 18–95 | HIGH |
| R03 | LOS outside 1–30 days | HIGH |
| R04 | LOS vs date diff mismatch | MEDIUM |
| R05 | BMI outside 10–60 | HIGH |
| R06 | Cost zero or negative | HIGH |
| R07 | Cost extreme outlier (>3×IQR) | MEDIUM |
| R08 | LOS extreme outlier (>20 days) | LOW |
| R09–R15 | Formatting, flags, audit columns | INFO |

### Step 3 — Feature Engineering
Transforms 36 clean columns into 72 model-ready features:

- Temporal features (9)
- Demographic bands (7)
- Binary clinical flags (13)
- Composite risk scores (4)
- Encoded categoricals (15)

### Step 4 — Predictive Modelling
Trains and evaluates three models:

| Model | AUC-ROC | Sensitivity | Specificity |
|-------|---------|-------------|-------------|
| Logistic Regression | 0.653 | 87.9% | 28.0% |
| Random Forest | 0.654 | 93.9% | 11.5% |
| Gradient Boosting ★ | 0.627 | 83.7% | 31.4% |

---

## Power BI Dashboard (6 Pages)

| Page | Content |
|------|---------|
| Executive Summary | KPI overview and navigation |
| Clinical Overview | Risk tiers, diagnosis rates, monthly trends |
| Risk Stratification | Patient watchlist with slicers |
| Cohort Trends | Age, payer, LOS trend analysis |
| Cost Impact | Cost by tier, diagnosis scatter |
| Hospital Benchmarking | Hospital comparison and feature importance |

---

## DAX Measures

| Measure | Purpose |
|---------|---------|
| Total Patients | Count of all patient encounters |
| Readmissions Count | Count of readmitted patients |
| Readmission Rate | Readmissions / Total patients |
| Critical Patients | Count of Critical-tier patients |
| Total Cost | Sum of all encounter costs |
| Avg Risk Score | Mean model risk score |
| Readmission Cost | Total cost of readmitted patients |
| Avg LOS | Average length of stay |

---

## Technologies Used

- Python 3.10
- pandas, numpy, scikit-learn
- Jupyter Notebook
- Power BI Desktop
- DAX (Data Analysis Expressions)

---

## How to Run

1. Clone the repository
2. Install dependencies:
