
# Day 1 — Finance Insights Analyst Project

## Project

Finance Insights Analyst Project — an end-to-end personal finance analytics project (Excel + SQL + Python + Stats + AI).

## Problem Statement

People have access to raw bank/UPI transaction data but no easy way to understand spending patterns, detect unusual transactions, or estimate future spend. This project turns raw transaction data into clean, structured, actionable insights.

## Today's Goal

Clean the raw transaction dataset and set it up for SQL-based analysis.

## Dataset

- Source: `Data_Analyst_Practice_Dataset_Dirty_10200.csv`
- Rows: 10,200 (before cleaning)
- Columns: Txn_ID, Date, Merchant, Category, Amount, Payment_Mode

## What I Did

### 1. Data Cleaning (Excel)

- Removed 200 duplicate rows
- Fixed inconsistent category spellings (Foood → Food, Groceires → Groceries,
  Medicl → Medical, Shoping → Shopping, Travell → Travel) using a lookup table
  with XLOOKUP + PROPER + TRIM
- Filled 294 missing Merchant values with "Unknown"
- Imputed missing Amount values using category-wise average (AVERAGEIF),
  with an Is_Imputed flag column for transparency
- Converted inconsistent date formats using DATEVALUE
- Built a 3-sheet workbook structure: Raw_Data → Cleaned_Data (formulas +
  pivot table) → Final (clean output ready for SQL/Python)

### 2. SQL Setup

- Created a `transactions` table in PostgreSQL
- Solved a date import issue: dates were importing as NULL due to a
  DD-MM-YYYY vs ISO format mismatch — fixed by standardizing the date
  format in Excel before export
- Wrote queries for: total spend, category-wise spend, payment mode
  breakdown, top merchants, and monthly spending trend
- Fixed a `date_trunc()` display issue (full timestamp with timezone)
  using `TO_CHAR()` for clean `YYYY-MM` output

## Formulas Used

| Formula           | Purpose                                                   |
| ----------------- | --------------------------------------------------------- |
| XLOOKUP + IFERROR | Fixing inconsistent category spellings via a lookup table |
| TRIM + PROPER     | Text standardization                                      |
| AVERAGEIF         | Category-wise mean imputation for missing amounts         |
| DATEVALUE         | Date format standardization                               |

## Key Learnings

- Learned how XLOOKUP + IFERROR can fix inconsistent categorical data
  without manually editing thousands of rows
- Learned that missing/messy data should never be silently deleted —
  it should be flagged and handled transparently (e.g. "Unknown" labels,
  Is_Imputed flags) so the treatment is auditable later
- Learned that PostgreSQL date import fails silently (returns NULL) if
  the format doesn't match what Postgres expects — always verify date
  formats before import

## Challenges Faced

- Date import was returning NULL in PostgreSQL due to a format mismatch —
  solved by standardizing the date format in Excel before exporting to CSV
- `date_trunc()` output showed a full timestamp with timezone info —
  fixed using `TO_CHAR()` for clean, readable monthly labels

## Tomorrow's Plan

Python EDA + statistical analysis (Z-score anomaly detection, forecasting)

## Links

- Project Repo: https://github.com/mmtiwari222/finance-insights-analyst-project
