# 📊 Statistics for Data Analysis — Day 1 Notes

> **Learning Track:** DA → DS → ML → AI | **Date:** June 27, 2026  
> **Author:** [@mmtiwari222](https://github.com/mmtiwari222) | Learning in public. Building in public.

---

## 📌 Topics Covered

- [What is Statistics?](#1-what-is-statistics)
- [Types of Statistics](#2-types-of-statistics)
- [Descriptive Statistics](#3-descriptive-statistics-intro)
- [Inferential Statistics](#4-inferential-statistics-intro)
- [Population vs Sample](#5-population-vs-sample)
- [Sampling Techniques](#6-sampling-techniques)
- [Variables & Types](#7-variables--types)
- [Qualitative vs Quantitative Data](#8-qualitative-categorical-data)
- [Histogram — Deep Dive](#10-histogram)

---

## 1. What is Statistics?

**Statistics** is the science of collecting, organizing, analyzing, interpreting, and presenting data to make informed decisions.

> 💡 Every data analyst uses statistics daily — from calculating average loan amounts to spotting trends in repayment behavior.

---

## 2. Types of Statistics

| Type | Purpose | Example |
|------|---------|---------|
| **Descriptive** | Summarize existing data | Avg EMI across 10K loan accounts |
| **Inferential** | Draw conclusions from a sample | Predict default rate from 500-customer sample |

---

## 3. Descriptive Statistics (Intro)

Summarizes the data you **already have**. Does NOT predict.

**Key Measures:**
- Central Tendency → Mean, Median, Mode
- Spread → Range, Variance, Standard Deviation
- Shape → Skewness, Kurtosis

---

## 4. Inferential Statistics (Intro)

Uses a **sample** to make conclusions about a larger **population**.

**Key Tools:** Hypothesis Testing, Confidence Intervals, Regression

> Example: Analyzing 300 borrower records to predict risk across 10,000 customers.

---

## 5. Population vs Sample

| Term | Definition | Example |
|------|-----------|---------|
| **Population** | Entire group to study | All 10,000 Sindhuja loan customers |
| **Sample** | Subset of population | 500 randomly chosen customers |
| **Parameter** | Metric of population | True avg income of all customers |
| **Statistic** | Metric of sample | Avg income from 500 sampled customers |

---

## 6. Sampling Techniques

### 🎯 Probability Sampling (Random — Less Bias)

| Technique | How it works | Example |
|-----------|-------------|---------|
| **Simple Random** | Equal chance for all | Random 100 loan IDs from 5000 |
| **Systematic** | Every nth record | Every 10th row in disbursement sheet |
| **Stratified** | Groups → sample each | Rural & Urban borrowers sampled separately |
| **Cluster** | Random clusters picked whole | Select 5 branches, take all their data |

### ⚠️ Non-Probability Sampling (Risk of Bias)

| Technique | How it works | Example |
|-----------|-------------|---------|
| **Convenience** | Easiest to access | Last month's ready data |
| **Judgmental** | Expert picks | Analyst selects high-risk profiles |
| **Snowball** | Existing subjects recruit new | Borrower referral chains |
| **Quota** | Fixed group sizes | Exactly 50M + 50F customers |

---

## 7. Variables & Types

```
Variable
├── Qualitative (Categorical)
│   ├── Nominal  → No order (Gender, Loan Type)
│   └── Ordinal  → Has order (Risk Level, Rating)
└── Quantitative (Numerical)
    ├── Discrete  → Countable (No. of loans)
    └── Continuous → Measurable (Loan amount ₹12,345.67)
```

---

## 8. Qualitative (Categorical) Data

### Nominal (No Order)
- Gender: Male / Female / Other
- Loan Type: Home / Personal / Business
- Branch: Delhi / Gurugram / Noida
- ❌ Cannot rank these

### Ordinal (Has Order)
- Credit Rating: Poor < Fair < Good < Excellent
- Risk Level: Low < Medium < High
- ✅ Can rank, but gaps between ranks ≠ equal

---

## 9. Quantitative Data

| Type | Definition | Example |
|------|-----------|---------|
| **Discrete** | Countable whole numbers | No. of loans per customer (1, 2, 3) |
| **Continuous** | Any value in a range | Loan amount ₹12,345.67, Rate 12.5% |

---

## 10. Histogram

### What is it?
A **bar chart for continuous/numerical data** showing **frequency distribution** of values grouped into bins.

> ⚠️ Key difference: Bar chart = categorical | Histogram = numerical/continuous

### Anatomy of a Histogram

| Component | Description |
|-----------|-------------|
| **X-axis** | Bins / intervals (e.g., ₹0–10K, ₹10K–25K) |
| **Y-axis** | Frequency (count of values in each bin) |
| **Bars** | Touch each other (no gaps!) |
| **Bin width** | Range each bar covers |

### How to Read Shape

```
Left-skewed  : ← long tail | data piled on RIGHT
Right-skewed : long tail → | data piled on LEFT  ← common in loan/income data
Symmetric    : Bell curve  | Normal distribution
```

### Real-World Example (Loan Data)

```
Loan Amount Distribution at Sindhuja Microcredit:
  ₹0 – ₹10K    → 120 customers
  ₹10K – ₹25K  → 450 customers  ← PEAK
  ₹25K – ₹50K  → 280 customers
  ₹50K+         →  50 customers
  
Conclusion: RIGHT-SKEWED → Mostly small-ticket loans
```

### Python Code

```python
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd

# Sample loan data
loan_amounts = [8000, 12000, 15000, 22000, 18000, 35000, 27000, 9000, 45000, 11000]

# Matplotlib
plt.figure(figsize=(8, 5))
plt.hist(loan_amounts, bins=5, color='steelblue', edgecolor='black')
plt.title('Loan Amount Distribution')
plt.xlabel('Loan Amount (₹)')
plt.ylabel('Frequency')
plt.show()

# Seaborn (better for EDA)
sns.histplot(loan_amounts, bins=5, kde=True, color='purple')
plt.title('Loan Amount Distribution with KDE')
plt.show()
```

---

## 🎯 Interview Q&A — Quick Revision

| Question | Answer |
|----------|--------|
| Descriptive vs Inferential? | Descriptive summarizes existing data. Inferential predicts about a population from a sample. |
| Best sampling for branch analysis? | Stratified — ensures all branches are represented. |
| Nominal vs Ordinal? | Nominal = no order (loan type). Ordinal = order but unequal gaps (risk level). |
| Histogram vs Bar Chart? | Histogram = continuous data, no gaps. Bar chart = categorical, has gaps. |
| What does right-skewed tell you? | Most values are low; a few very high values pull the tail right. Common in income/loan data. |

---

## 🔗 Connect

- 🐙 GitHub: [@mmtiwari222](https://github.com/mmtiwari222)
- 💼 LinkedIn: Learning in public. Building in public.
- 🏢 IT Analyst → Data Analyst

---

*Part of my public DA → DS → ML → AI learning journey. One day at a time. 🚀*
