
# Day 2 — Finance Insights Analyst Project

## Today's Goal

Perform EDA, detect anomalies using statistics, and forecast next month's spend using Python.

## What I Did

### 1. Data Load & Validation

- Loaded cleaned CSV into Pandas, converted Date to datetime
- Discovered Amount still had missing values despite Excel cleaning
  (an export step had dropped the imputed column) — handled it directly
  in Python instead

### 2. Missing Value Handling (Python)

- Created an `Is_Imputed` flag column BEFORE filling missing values,
  so real vs. estimated values remain distinguishable
- Imputed missing amounts using category-wise mean (`groupby` + `transform`)
- Verified the imputation using `value_counts()` on the flag column

### 3. Exploratory Data Analysis

- Computed category-wise total, average, and count of transactions
- Highest spend category: Food (₹56.3L), followed by Medical and Shopping
- Built a sorted bar chart for category-wise spend

### 4. Z-Score Anomaly Detection

- Calculated category-wise Z-score: `(x - mean) / std`
- Flagged transactions with |Z-score| > 3 as anomalies
- Found 94 anomalies out of 10,000 transactions (~0.9%)
- Highest anomaly: ₹1,99,607 Entertainment transaction (Z-score ~15)

### 5. Monthly Trend & Forecast

- Identified January 2026 as an incomplete month (only 1 day of data)
  and excluded it from trend analysis and forecasting
- Built a monthly spend trend chart (Jan–Dec 2025)
- Calculated three separate forecasts to isolate the effect of each
  data issue independently, rather than assuming errors cancel out:
  - Naive forecast (incomplete month included): ₹21,97,945.92
  - Complete months only, anomalies still included: ₹29,94,059.49
  - Final forecast (complete months, anomalies excluded): ₹21,66,594.80
- Anomalies alone were inflating the forecast by ₹8,27,464.69 (~38%)

### 6. Additional Checks

- Payment mode usage is fairly evenly distributed across categories —
  no single mode dominates
- Near-zero correlation (r = 0.02) between transaction amount and
  day of the month

## Formulas/Functions Used

| Function                            | Purpose                                             |
| ----------------------------------- | --------------------------------------------------- |
| `groupby().transform()`           | Category-wise mean imputation & Z-score calculation |
| `isna()`                          | Flagging missing values before imputation           |
| `to_period("M")`                  | Monthly aggregation                                 |
| `pd.options.display.float_format` | Fixing scientific notation in output                |

## Key Learnings

- Learned that notebook cells carry state — a kernel restart requires
  re-running cells top to bottom in order, or logic errors happen silently
- Learned to flag imputed values before filling them (order matters for
  transparency)
- Learned to identify and exclude incomplete time periods from trend
  analysis to avoid skewed forecasts
- Learned that two data-quality issues can accidentally offset each
  other's effect on a result — a forecast that "looks right" isn't the
  same as one that's methodologically correct. Each issue needs to be
  identified and corrected independently
- Learned that "no correlation" is also a valid, reportable insight

## Challenges Faced

- Amount had missing values in Python despite being "fixed" in Excel —
  root cause was the Excel export step, not the formula itself. Solved
  by imputing directly in Python with an `Is_Imputed` flag for transparency
- Chart bars were sorting alphabetically instead of by value — fixed by
  explicitly reassigning the sorted dataframe before plotting
- Scientific notation in output (e.g. 5.629692e+06) — fixed using
  `pd.options.display.float_format`
- A variable-naming bug caused two different forecast calculations to
  overwrite the same variable name, producing a misleading comparison —
  fixed by giving each forecast version its own clearly named variable

## Tomorrow's Plan

AI-powered insight generation (Gemini API) + final dashboard

## Links

- Project Repo: https://github.com/mmtiwari222/finance-insights-analyst-project
