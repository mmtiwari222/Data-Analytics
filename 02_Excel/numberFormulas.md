# 🔢 Excel Number Formulas — Complete Reference

> **Madanmohan Tiwari** | IT Analyst → AI-Powered Data Analyst  
> Sindhuja Microcredit, Gurugram | June 2026

Complete reference for all Excel number and math formulas — with syntax, examples, real-world use cases, and interview Q&A.

---

## 📋 Table of Contents

- [Why number formulas matter](#-why-number-formulas-matter)
- [Category 1 — Basic Math](#category-1--basic-math)
- [Category 2 — Rounding](#category-2--rounding)
- [Category 3 — Statistics](#category-3--statistics)
- [Category 4 — Conditional Math](#category-4--conditional-math)
- [Category 5 — Rank and Percentile](#category-5--rank-and-percentile)
- [Category 6 — Finance](#category-6--finance)
- [Power Combinations](#-power-combinations--real-world-formulas)
- [Interview Q&A](#-interview-qa)
- [Quick Reference Table](#-quick-reference-table)

---

## 💡 Why Number Formulas Matter

Number formulas are the engine of Excel. From summing loan disbursements to calculating EMIs, from ranking customers to finding outliers — every Data Analyst uses these daily. These formulas turn raw numbers into business insight.

---

## Category 1 — Basic Math

### `SUM(number1, [number2], ...)`
Adds all numbers in a range. Most-used formula in Excel.

```excel
=SUM(A1:A10)              → adds all values A1 to A10
=SUM(A1, B1, C1)          → adds individual cells
=SUM(A1:A10, C1:C10)      → adds two separate ranges
```

> **Shortcut:** `Alt + =` auto-inserts SUM for a selected range.

---

### `PRODUCT(number1, [number2], ...)`
Multiplies all numbers in a range together.

```excel
=PRODUCT(A1:A5)           → same as =A1*A2*A3*A4*A5
=PRODUCT(2, 3, 4)         → 24
```

---

### `MOD(number, divisor)`
Returns the remainder after division.

```excel
=MOD(10, 3)               → 1
=MOD(A2, 2)=0             → TRUE if A2 is even
=MOD(ROW(), 2)=0          → alternate row shading in conditional formatting
```

> **Use case:** Check even/odd numbers, create banded row highlighting.

---

### `ABS(number)`
Returns the absolute (always positive) value.

```excel
=ABS(-500)                → 500
=ABS(A2-B2)               → difference regardless of direction
```

---

### `POWER(number, power)` / `SQRT(number)`

```excel
=POWER(2, 10)             → 1024
=SQRT(144)                → 12
```

---

## Category 2 — Rounding

Critical for financial reporting — EMIs, interest rates, and percentages need precise display.

### `ROUND(number, num_digits)`
Standard mathematical rounding (0.5 rounds up).

```excel
=ROUND(3.567, 2)          → 3.57
=ROUND(3.564, 2)          → 3.56
=ROUND(1234, -2)          → 1200  ← negative digits = round to 100s
=ROUND(A2, 0)             → nearest whole number
```

---

### `ROUNDUP(number, num_digits)`
Always rounds away from zero — never down.

```excel
=ROUNDUP(3.21, 1)         → 3.3
=ROUNDUP(3.01, 1)         → 3.1
=ROUNDUP(2.001, 0)        → 3
```

> **Use case:** EMI ceiling — always round the payment up so borrower doesn't underpay.

---

### `ROUNDDOWN(number, num_digits)`
Always rounds toward zero — truncates.

```excel
=ROUNDDOWN(3.99, 1)       → 3.9
=ROUNDDOWN(3.99, 0)       → 3
```

---

### `INT(number)` / `TRUNC(number, [digits])`

```excel
=INT(3.9)                 → 3
=INT(-3.1)                → -4    ← rounds toward negative infinity
=TRUNC(3.987, 1)          → 3.9   ← just cuts, no rounding
=TRUNC(-3.987, 1)         → -3.9  ← toward zero (unlike INT)
```

### Rounding comparison table

| Function | 3.5 | -3.5 | Behavior |
|---|---|---|---|
| ROUND | 4 | -4 | Standard math |
| ROUNDUP | 4 | -4 | Always away from zero |
| ROUNDDOWN | 3 | -3 | Always toward zero |
| INT | 3 | -4 | Toward negative infinity |
| TRUNC | 3 | -3 | Toward zero |

---

## Category 3 — Statistics

### `AVERAGE(range)`
Arithmetic mean — ignores text and blank cells.

```excel
=AVERAGE(A1:A20)
=AVERAGE(A1:A20, C1:C20)
```

> ⚠️ AVERAGE ignores blanks but **includes zeros**. Use AVERAGEIF to exclude zeros.

---

### `COUNT` / `COUNTA` / `COUNTBLANK`

```excel
=COUNT(A1:A100)           → counts cells with numbers only
=COUNTA(A1:A100)          → counts all non-empty cells (text + numbers)
=COUNTBLANK(A1:A100)      → counts empty cells
```

| Function | What it counts |
|---|---|
| COUNT | Numbers only |
| COUNTA | Any non-empty cell |
| COUNTBLANK | Empty cells only |

---

### `MAX(range)` / `MIN(range)`

```excel
=MAX(A1:A100)             → highest value
=MIN(A1:A100)             → lowest value
=MAX(A1:A100)-MIN(A1:A100) → spread / range
```

---

### `MEDIAN(range)` / `MODE(range)`

```excel
=MEDIAN(A1:A100)          → middle value when sorted
=MODE(A1:A100)            → most frequently occurring value
```

> **Interview tip:** Use MEDIAN for loan or income data where outliers would distort AVERAGE.

---

### `LARGE(array, k)` / `SMALL(array, k)`
kth largest or smallest value — more flexible than MAX/MIN.

```excel
=LARGE(A1:A100, 1)        → largest (same as MAX)
=LARGE(A1:A100, 3)        → 3rd largest
=SMALL(A1:A100, 2)        → 2nd smallest
```

---

## Category 4 — Conditional Math

The most important formulas for Data Analysts — compute values based on conditions.

### `SUMIF(range, criteria, [sum_range])`
Sums cells that meet **one condition**.

```excel
=SUMIF(B:B, "Delhi", C:C)         → total where branch = Delhi
=SUMIF(C:C, ">50000", C:C)        → sum of amounts > 50,000
=SUMIF(D:D, "Active", C:C)        → sum of active loans
=SUMIF(B:B, "*Gurg*", C:C)        → wildcard: contains "Gurg"
```

---

### `SUMIFS(sum_range, range1, c1, range2, c2, ...)`
Sum with **multiple conditions** — AND logic. Note: `sum_range` comes **FIRST**.

```excel
=SUMIFS(C:C, B:B, "Delhi", D:D, "Active")
→ total active loans in Delhi

=SUMIFS(C:C, B:B, "Gurugram", C:C, ">50000")
→ Gurugram loans above 50,000
```

---

### `COUNTIF(range, criteria)`
Counts cells matching **one condition**.

```excel
=COUNTIF(D:D, "Active")           → count active loans
=COUNTIF(C:C, ">50000")          → loans above 50,000
=COUNTIF(B:B, "Delhi")           → Delhi branch entries
```

---

### `COUNTIFS(range1, c1, range2, c2, ...)`
Count with **multiple conditions** — AND logic.

```excel
=COUNTIFS(B:B, "Delhi", D:D, "Active")
→ active Delhi loans

=COUNTIFS(B:B, "Gurugram", C:C, ">50000", D:D, "Closed")
→ closed Gurugram loans above 50,000
```

---

### `AVERAGEIF` / `AVERAGEIFS`

```excel
=AVERAGEIF(B:B, "Delhi", C:C)
=AVERAGEIFS(C:C, B:B, "Delhi", D:D, "Active")
```

### Argument order — critical!

| Formula | Argument order |
|---|---|
| SUMIF | range, criteria, **sum_range** |
| SUMIFS | **sum_range**, range1, c1, range2, c2... |
| COUNTIF | range, criteria |
| COUNTIFS | range1, c1, range2, c2... |

---

## Category 5 — Rank and Percentile

### `RANK(number, ref, [order])`
Rank of a number within a list. `0` = descending, `1` = ascending.

```excel
=RANK(B2, B:B, 0)
=RANK(B2, $B$2:$B$100, 0)    ← use $ when copying down
```

---

### `PERCENTILE(array, k)`
Value at the kth percentile. k is between 0 and 1.

```excel
=PERCENTILE(A1:A100, 0.9)    → 90th percentile
=PERCENTILE(A1:A100, 0.5)    → median (50th percentile)
=PERCENTILE(A1:A100, 0.25)   → Q1
```

---

### `QUARTILE(array, quart)`

```excel
=QUARTILE(A1:A100, 1)        → Q1 (25th percentile)
=QUARTILE(A1:A100, 2)        → Q2 / median
=QUARTILE(A1:A100, 3)        → Q3 (75th percentile)
```

---

## Category 6 — Finance

### `PMT(rate, nper, pv)`
Monthly EMI payment on a loan.

```excel
=PMT(8%/12, 60, -500000)
→ monthly EMI on ₹5,00,000 at 8% for 5 years

Arguments:
  rate  = annual_rate / 12    (monthly interest)
  nper  = tenure in months
  pv    = -principal          (negative = cash going out)
```

---

### `FV(rate, nper, pmt, [pv])`
Future value of an investment.

```excel
=FV(6%/12, 60, -5000, 0)
→ value of ₹5,000/month invested for 5 years at 6%
```

---

### `NPV(rate, value1, ...)` / `IRR(values)` / `RATE(nper, pmt, pv)`

```excel
=NPV(10%, B2:B7)              → present value of future cash flows
=IRR(B2:B7)                   → effective annual return
=RATE(60, -10000, 500000)*12  → annual interest rate
```

---

## ⚡ Power Combinations — Real-World Formulas

### Loan portfolio analysis
```excel
Branch total disbursement:
=SUMIF(Branch_col, "Delhi", Amount_col)

Active loans above threshold:
=COUNTIFS(Status_col, "Active", Amount_col, ">50000")

Average active loan in branch:
=AVERAGEIFS(Amount_col, Branch_col, "Delhi", Status_col, "Active")

Top 5 loan amounts:
=LARGE(Amount_col, 1)   through   =LARGE(Amount_col, 5)
```

### EMI and financial calculations
```excel
EMI calculation:
=PMT(interest_rate/12, tenure_months, -principal)

Repayment rate %:
=ROUND(collected/total*100, 2)

Growth rate:
=(New - Old) / ABS(Old) * 100

Round to nearest 500:
=ROUND(A2/500, 0) * 500
```

### Statistical analysis
```excel
90th percentile loan amount:
=PERCENTILE(Amount_col, 0.9)

Rank customers by loan amount:
=RANK(B2, $B$2:$B$100, 0)

Count non-empty data rows:
=COUNTA(A:A)-1

Alternate row coloring (conditional format formula):
=MOD(ROW(), 2)=0
```

---

## 🎯 Interview Q&A

**Q1. What is the difference between SUMIF and SUMIFS?**

SUMIF handles one condition; SUMIFS handles multiple. Critical syntax difference: in SUMIF, `sum_range` is the 3rd argument. In SUMIFS, `sum_range` is the **1st** argument.

---

**Q2. What is the difference between COUNT, COUNTA, and COUNTBLANK?**

COUNT counts cells with numbers only. COUNTA counts any non-empty cell (text or numbers). COUNTBLANK counts empty cells.

---

**Q3. What is the difference between ROUND, ROUNDUP, and ROUNDDOWN?**

ROUND uses standard math (0.5 rounds up). ROUNDUP always rounds away from zero. ROUNDDOWN always truncates toward zero.

---

**Q4. When would you use MEDIAN instead of AVERAGE?**

When data has outliers. For loan or income data, a few very large values inflate the AVERAGE. MEDIAN gives the middle value and is unaffected by extremes.

---

**Q5. How does MOD work and what is it used for?**

MOD returns the remainder after division. `=MOD(A2, 2)=0` checks if a number is even. Used in conditional formatting (`=MOD(ROW(),2)=0`) to create alternating row colors.

---

**Q6. What does PMT return and what are its arguments?**

PMT returns the fixed periodic payment (EMI) on a loan.  
`=PMT(8%/12, 60, -500000)` → monthly EMI on ₹5,00,000 at 8% for 5 years.  
Arguments: rate per period, total periods, present value (negative).

---

**Q7. How do you find the top 3 values in a column?**

```excel
=LARGE(Amount_col, 1)     → highest
=LARGE(Amount_col, 2)     → 2nd highest
=LARGE(Amount_col, 3)     → 3rd highest
```

---

**Q8. What is the difference between INT and TRUNC for negative numbers?**

For positives they behave the same. For negatives: `=INT(-3.1)` returns `-4` (toward negative infinity), but `=TRUNC(-3.1)` returns `-3` (toward zero).

---

## 📊 Quick Reference Table

| Formula | Purpose | Key Note |
|---|---|---|
| `SUM` | Add range | `Alt + =` shortcut |
| `PRODUCT` | Multiply range | — |
| `MOD` | Remainder | Check even/odd |
| `ABS` | Absolute value | Removes sign |
| `POWER` / `SQRT` | Exponent / Root | — |
| `ROUND` | Standard rounding | Negative digits = 10s/100s |
| `ROUNDUP` | Always rounds up | EMI ceiling |
| `ROUNDDOWN` | Always truncates | — |
| `INT` | Integer toward -inf | Different from TRUNC for negatives |
| `AVERAGE` | Arithmetic mean | Ignores blanks, includes zeros |
| `COUNT` | Count numbers | — |
| `COUNTA` | Count non-empty | Includes text |
| `MAX` / `MIN` | Highest / Lowest | — |
| `MEDIAN` | Middle value | Better for skewed data |
| `LARGE` / `SMALL` | kth largest/smallest | More flexible than MAX/MIN |
| `SUMIF` | Sum one condition | sum_range is 3rd arg |
| `SUMIFS` | Sum multi-condition | sum_range is **1st** arg |
| `COUNTIF` | Count one condition | — |
| `COUNTIFS` | Count multi-condition | — |
| `RANK` | Rank in list | 0=desc, 1=asc |
| `PERCENTILE` | kth percentile | k from 0 to 1 |
| `QUARTILE` | Q1/Q2/Q3/Q4 | quart: 1, 2, 3, 4 |
| `PMT` | Loan EMI | rate/12, months, -principal |
| `FV` | Future value | — |
| `NPV` | Net present value | — |
| `IRR` | Rate of return | — |

---

## 📁 Repository Structure

```
📁 excel-learning/
├── 01-home-tab/
│   └── README.md
├── 02-text-formulas/
│   └── README.md
├── 03-number-formulas/
│   └── README.md          ← You are here
└── assets/
    └── excel_number_formulas.jpg
```

---

## 🛠️ Tech Stack

![Excel](https://img.shields.io/badge/Microsoft_Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![Notion](https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white)

---

## 👤 About Me

**Madanmohan Tiwari**  
IT Analyst @ Sindhuja Microcredit, Gurugram  
Learning path: `Data Analyst` → `Data Science` → `ML` → `Gen AI` → `Agentic AI`

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/madanmohan-tiwari)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/mmtiwari222)

---

*Learning in public. Building in public. One formula at a time.* 🚀
