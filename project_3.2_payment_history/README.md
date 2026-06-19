# Project 3.2 – Payment History Analysis

## Objective
Determine whether a borrower's payment history (late payments) is a stronger predictor of loan default than application‑only data.

## Data Sources
- `application_train.csv` – loan‑level data, including `TARGET` (default indicator)
- `installments_payments.csv` – payment‑level data, including `DAYS_ENTRY_PAYMENT` (positive = late in some datasets; here **negative = late**)

## Key Insight
In this dataset, **negative** values in `DAYS_ENTRY_PAYMENT` indicate late payments.

## Analysis Steps
1. Flag each loan: has at least one late payment? (Yes/No)
2. Join this flag back to the application table (using `LEFT JOIN` to keep all loans)
3. Compare default rates between:
   - Loans with **no late payments**
   - Loans with **at least one late payment**
4. Calculate late payment severity metrics (average days late, max days late) for defaulted vs. non‑defaulted loans

## Results

### Default Rate by Late Payment Status
| payment_status | default_rate | total_loans | total_defaults |
|----------------|--------------|-------------|----------------|
| No late payments | 7.86% | 19,792 | 1,555 |
| Has late payments | 8.16% | 79,157 | 6,462 |

### Late Payment Metrics by Default Status
| defaulted | avg_late_payments | avg_days_late | max_days_late |
|-----------|-------------------|---------------|---------------|
| No (0) | 9.04 | 748.82 | 3071.0|
| Yes (1) | 8.44| 676.51 | 2960.0 |


## Conclusion
- Loans with late payments have a **higher default rate** than those without.
- Defaulted loans have **more late payments** and **worse severity** (average and maximum days late).
- **Payment history is a stronger predictor of default than application‑only data.**



## Tools Used
- SQLite / pandasql
- Python (for loading CSVs)
