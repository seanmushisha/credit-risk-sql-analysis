# Project 3.3 – Risk Dashboard Queries

## Objective
Write a set of clean, reusable SQL queries that would feed a Tableau / Power BI dashboard for a credit risk team.

Unlike exploratory queries (3.1, 3.2), these are designed to be **scheduled**, **automated**, and **dashboard‑ready** 

## Queries Included

| # | Query Name | Purpose | Dashboard Use |
|---|------------|---------|---------------|
| 1 | Portfolio KPIs | One‑row summary: total loans, defaults, default rate, avg loan amount, avg income | KPI cards at the top of the dashboard |
| 2 | Default rate by age group | Shows how default risk varies with borrower age | Bar chart or line chart |
| 3 | Income × Age risk grid | Heatmap‑style breakdown for risk segmentation | Heatmap / table for risk team review |
| 4 | High‑risk flags | Loans flagged as high risk based on rules | Watch list table for manual review |
| 5 | Late payment summary | Default rate by late payment status | Key insight card or bar chart |

---

## Query Details

### Query 1 – Portfolio KPIs
- **Columns:** `total_loans`, `total_defaults`, `default_rate`, `avg_loan_amount`, `avg_income`
- **Use:** Top‑level dashboard numbers

### Query 2 – Default Rate by Age Group
- **Columns:** `age_group`, `total_loans`, `total_defaults`, `default_rate`
- **Bins:** Young (18–30), Mid (31–40), Mature (41–50), Senior (51+)
- **Use:** Shows which age segments are riskiest

### Query 3 – Income × Age Grid
- **Columns:** `income_bracket`, `age_group`, `total_loans`, `total_defaults`, `default_rate`
- **Income bins:** Low (<50k), Medium (50k–100k), High (100k–150k), Very High (>150k)
- **Use:** Heatmap — quickly spot high‑risk segments

### Query 4 – High‑Risk Flags
- **Columns:** `SK_ID_CURR`, `income`, `loan_amount`, `age`, `has_late_payment`, `high_risk_flag`
- **Rules:** Income < 30k AND age < 25 OR loan > 150k OR has late payment
- **Use:** Watch list — loans that need manual review

### Query 5 – Late Payment Summary
- **Columns:** `payment_status`, `total_loans`, `total_defaults`, `default_rate`
- **Use:** Key insight card showing impact of payment history on default

---

## Technical Notes

- **Data Source:** `application_train.csv` + `installments_payments.csv`
- **Method:** SQLite was used to handle large joins without memory issues
- **Outputs:** CSVs ready for Tableau / Power BI

## Outputs
- `query_4_high_risk.csv`
- `query_6_payment_history_analysis.csv`

## Business Value
These queries give a risk team a live view of:
- Overall portfolio health (KPIs)
- Risk trends by customer segment (age, income)
- High‑risk loans that need attention
- The impact of payment behavior on default
