# 📐 Statistics Day 2 — Distribution, Central Tendency, Dispersion, Percentiles & Box Plot

> **Learning Track:** DA → DS → ML → AI | **Date:** June 29, 2026
> **Author:** [@mmtiwari222](https://github.com/mmtiwari222) | Domain: BFSI / Microfinance
> Learning in public. Building in public. 🚀

---

## 📌 Topics Covered

| # | Topic |
|---|-------|
| 1 | [Distribution & Range](#1-distribution--range) |
| 2 | [Measures of Central Tendency](#2-measures-of-central-tendency) |
| 3 | [Mean](#21-mean) |
| 4 | [Median](#22-median) |
| 5 | [Mode](#23-mode) |
| 6 | [Outlier](#3-outlier) |
| 7 | [Dispersion & Variance](#4-dispersion--variance) |
| 8 | [Bessel's Correction & Degrees of Freedom](#42-bessels-correction--degrees-of-freedom) |
| 9 | [Standard Deviation](#43-standard-deviation) |
| 10 | [Percentile & Quartiles](#5-percentile--quartiles) |
| 11 | [Five-Number Summary](#6-five-number-summary) |
| 12 | [Box Plot](#7-box-plot) |
| 13 | [Interview Q&A](#interview-qa) |

---

## 1. Distribution & Range

### Distribution
Describes how values are **spread or arranged** across a range.

| Shape | Description | Real Example |
|-------|-------------|--------------|
| **Normal/Symmetric** | Bell curve, Mean = Median = Mode | Heights of people |
| **Right-skewed (+)** | Long tail on right, Mean > Median | Loan amounts, Income |
| **Left-skewed (−)** | Long tail on left, Mean < Median | Exam scores (when easy) |
| **Uniform** | All values equally likely | Dice rolls |
| **Bimodal** | Two peaks | Salary in a company (junior + senior) |

> 💡 **Always** describe distribution shape before choosing a central tendency measure.

### Range
```
Range = Maximum − Minimum
```

**BFSI Example:**
```
Loan amounts: ₹5,000 | ₹12,000 | ₹18,000 | ₹25,000 | ₹95,000
Range = ₹95,000 − ₹5,000 = ₹90,000
```
> ⚠️ **Limitation:** Heavily inflated by outliers. One large loan skews the entire range.

---

## 2. Measures of Central Tendency

A single value that represents the **center** of the data.

| Measure | Population Symbol | Sample Symbol | Resistant to Outliers? |
|---------|------------------|---------------|------------------------|
| **Mean** | μ (mu) | x̄ (x-bar) | ❌ No |
| **Median** | M | M | ✅ Yes |
| **Mode** | — | — | ✅ Yes |

---

### 2.1 Mean

**Formula:**
```
Population Mean:  μ  = Σx / N
Sample Mean:      x̄  = Σx / n
```

**When to use:**
- Normally distributed data with no extreme outliers
- Further statistical computation (variance, SD, regression)

**When NOT to use:**
- Skewed data → use Median instead
- Presence of outliers → mean gets misleadingly pulled

**BFSI Real Use Case:**
```
EMIs: ₹10K, ₹12K, ₹15K, ₹18K, ₹20K
Mean = (10+12+15+18+20) / 5 = ₹15,000  ✅ Fair representation

# With outlier:
EMIs: ₹10K, ₹12K, ₹15K, ₹18K, ₹2,00,000
Mean = ₹51,000  ❌ Misleading! One corporate loan ruins the metric
Median = ₹15,000  ✅ Use this instead
```

```python
import numpy as np
emi = [10000, 12000, 15000, 18000, 200000]
print(f"Mean:   ₹{np.mean(emi):,.0f}")    # ₹51,000 — skewed!
print(f"Median: ₹{np.median(emi):,.0f}")  # ₹15,000 — better!
```

> 💡 **Interview Tip:** *"In BFSI data, I always check for outliers before using mean. One large corporate loan in a personal loan dataset will completely distort the average."*

---

### 2.2 Median

The **middle value** when data is sorted ascending.
- Odd count → middle value
- Even count → average of two middle values

**When to use:**
- Skewed distributions (income, loan amounts, property prices)
- Data with outliers
- Ordinal data

**BFSI Real Use Case:**
```
Sorted loans: ₹8K, ₹11K, ₹15K, ₹22K, ₹1,50,000
Median = ₹15,000  (3rd value, not affected by ₹1.5L outlier)

Even count: ₹8K, ₹11K, ₹15K, ₹22K
Median = (₹11K + ₹15K) / 2 = ₹13,000
```

> 💡 **Interview Tip:** *"Median household income of borrowers is a better metric than mean income — it's robust to the few high-income outliers that skew the distribution."*

---

### 2.3 Mode

The **most frequently occurring** value.

| Type | Description | Example |
|------|-------------|---------|
| **Unimodal** | One mode | Most customers borrow ₹15K |
| **Bimodal** | Two modes | Peak demand at ₹10K and ₹25K |
| **No mode** | All values unique | Every loan amount is different |

**When to use:**
- **Categorical/Nominal data** → Mode is the ONLY valid central tendency measure
- Finding most popular product, branch, or repayment day

**BFSI Real Use Cases:**
| Scenario | Mode Result |
|----------|-------------|
| Most common loan product | Personal Loan |
| Most frequent repayment day | 5th of month |
| Most visited branch | Gurugram Main |
| Most common loan tenure | 24 months |

```python
from scipy import stats
loans = [10000, 15000, 15000, 20000, 15000, 25000]
result = stats.mode(loans)
print(f"Mode: ₹{result.mode:,} (appears {result.count} times)")
```

---

## 3. Outlier

A data point **significantly different** from the rest of the dataset.

### Detection Methods

| Method | Formula / Tool | Threshold |
|--------|---------------|-----------|
| **IQR Method** | Below Q1−1.5×IQR or above Q3+1.5×IQR | Standard |
| **Z-score** | Z = (x − μ) / σ | \|Z\| > 3 |
| **Visual** | Box plot | Dots beyond whiskers |

### Impact on Measures

| Measure | Affected by Outlier? |
|---------|---------------------|
| Mean | ✅ Yes — heavily pulled |
| Median | ❌ No — robust |
| Mode | ❌ No — unaffected |
| Range | ✅ Yes — inflated |
| Variance & SD | ✅ Yes — inflated |
| IQR | ❌ No — robust |

> ⚠️ **Always ask:** Is this a data entry error or a valid extreme value? Treatment depends on business context.

---

## 4. Dispersion & Variance

### Dispersion
Measures how **spread out** values are around the center.

```
Dataset A: ₹14K, ₹15K, ₹16K  → Mean = ₹15K, Low spread
Dataset B: ₹5K,  ₹15K, ₹25K  → Mean = ₹15K, HIGH spread
```
> Same mean, completely different behavior!

---

### 4.1 Variance

Average of **squared differences** from the mean.

```
Population Variance:  σ² = Σ(xᵢ − μ)²  / N
Sample Variance:      s² = Σ(xᵢ − x̄)² / (n−1)   ← Bessel's Correction
```

**Step-by-Step Calculation:**
```
EMIs: ₹2K, ₹3K, ₹4K, ₹5K, ₹6K
Mean (x̄) = ₹4K

Deviations:        −2, −1,  0, +1, +2
Squared devs:       4,  1,  0,  1,  4
Sum of squares = 10

Population σ² = 10 / 5    = 2.0  (₹K²)
Sample     s² = 10 / (5−1) = 2.5  (₹K²)  ← Bessel's correction
```

> ⚠️ Variance is in **squared units** (₹²) — hard to interpret. That's why we use Standard Deviation.

---

### 4.2 Bessel's Correction & Degrees of Freedom

**The Problem:**
Sample variance with divisor `n` systematically **underestimates** true population variance, because sample values cluster closer to the sample mean than to the true population mean.

**Bessel's Correction:**
```
Biased (wrong):   s² = Σ(x − x̄)² / n
Unbiased (right): s² = Σ(x − x̄)² / (n−1)  ← Bessel's Correction
```

**Degrees of Freedom:**
- With `n` data points and a known sample mean, only `n−1` values are free to vary
- The last value is fully determined by the others once the mean is fixed
- Therefore, only `n−1` independent pieces of information exist → divide by `n−1`

**Quick Example:**
```
3 values with mean = 10
If values are: 8, 12, ?
Then 3rd value MUST be 10 → it's not free
df = 3 − 1 = 2
```

> 💡 **Interview Answer:** *"Bessel's correction adjusts for the fact that sample deviations from the sample mean are smaller than deviations from the true population mean. Dividing by n−1 compensates for this bias and gives an unbiased estimator."*

---

### 4.3 Standard Deviation

Square root of variance — brings units back to the **original scale**.

```
Population SD:  σ = √[Σ(xᵢ − μ)²  / N]
Sample SD:      s = √[Σ(xᵢ − x̄)² / (n−1)]
```

**From our example:**
```
Sample Variance s² = 2.5 ₹K²
Sample SD s = √2.5 ≈ ₹1.58K

Mean EMI = ₹4K ± ₹1.58K → Typical range: ₹2.42K to ₹5.58K
```

**The Empirical Rule (Normal Distribution):**
```
μ ± 1σ  →  ~68% of data
μ ± 2σ  →  ~95% of data
μ ± 3σ  →  ~99.7% of data
```

**BFSI Real Use Cases:**

| Use Case | What SD Tells You |
|----------|-------------------|
| EMI payment amounts | Low SD = consistent customers; High SD = varied risk profiles |
| Monthly disbursements per branch | Low SD = stable operations; High SD = erratic lending |
| Loan processing time | High SD = inconsistent processes, needs SOP review |
| Credit score distribution | SD helps define risk bands (Low/Medium/High risk) |

```python
import numpy as np

emi = [2000, 3000, 4000, 5000, 6000]

print(f"Mean:              ₹{np.mean(emi):,.0f}")
print(f"Population Var σ²: {np.var(emi, ddof=0):,.2f}")
print(f"Sample Var     s²: {np.var(emi, ddof=1):,.2f}")   # ddof=1 → Bessel's correction
print(f"Population SD  σ:  ₹{np.std(emi, ddof=0):,.2f}")
print(f"Sample SD      s:  ₹{np.std(emi, ddof=1):,.2f}")  # ddof=1 → Bessel's correction
```

> 💡 **Interview Tip:** *"In numpy, always use `ddof=1` for sample standard deviation. Default `ddof=0` gives population SD. This is a very common mistake in take-home assignments."*

---

## 5. Percentile & Quartiles

### Percentile

Value below which a **certain % of observations** fall.

```
Pk = k-th percentile
P50 = Median (50% of data below)
P25 = Q1     (25% of data below)
P75 = Q3     (75% of data below)
P90          (90% of data below) → used for risk thresholds
```

**Calculation:**
```
Step 1: Sort data ascending
Step 2: L = (k / 100) × n
Step 3: If L is whole → average of Lth & (L+1)th values
        If L is decimal → round up → value at that position
```

**BFSI Example (P90 of loan amounts):**
```
Sorted (n=10): ₹5K,₹8K,₹10K,₹12K,₹15K,₹18K,₹22K,₹25K,₹30K,₹50K
L = 0.90 × 10 = 9 → P90 = avg(9th, 10th) = (30+50)/2 = ₹40K
Interpretation: 90% of customers borrow less than ₹40K
```

> 💡 **Use Case:** Credit risk teams set P95 loan amount as the exposure cap. HR uses P75 to benchmark salaries.

---

### Quartiles

Divide sorted data into **4 equal parts**.

| Quartile | = Percentile | Meaning |
|----------|-------------|---------|
| **Q1** | P25 | Lower quartile — 25% below |
| **Q2** | P50 | Median — 50% below |
| **Q3** | P75 | Upper quartile — 75% below |
| **IQR** | Q3 − Q1 | Middle 50% spread |

**Outlier Detection with IQR:**
```
Lower fence = Q1 − 1.5 × IQR
Upper fence = Q3 + 1.5 × IQR
Any value outside these fences = OUTLIER
```

**BFSI Example:**
```
Sorted EMIs: ₹1K,₹2K,₹3K,₹4K,₹5K,₹6K,₹7K,₹8K
Q1  = ₹2.5K
Q2  = ₹4.5K  (Median)
Q3  = ₹6.5K
IQR = ₹4K

Lower fence = 2.5 − 1.5×4 = −₹3.5K  → No outliers on low end
Upper fence = 6.5 + 1.5×4 = ₹12.5K  → Any EMI > ₹12.5K = OUTLIER
```

---

## 6. Five-Number Summary

The most compact description of a dataset.

| # | Statistic | Symbol |
|---|-----------|--------|
| 1 | Minimum | Min |
| 2 | First Quartile | Q1 |
| 3 | Median | Q2 |
| 4 | Third Quartile | Q3 |
| 5 | Maximum | Max |

**BFSI Example — Loan Portfolio Summary:**
```
Min    = ₹5,000
Q1     = ₹12,000
Median = ₹18,000
Q3     = ₹28,000
Max    = ₹1,20,000

IQR    = ₹16,000
Range  = ₹1,15,000

→ Middle 50% of loans: ₹12K–₹28K
→ Upper fence: ₹28K + 1.5×16K = ₹52K → Max ₹1.2L is an OUTLIER
→ Median closer to Q1 → Right-skewed (as expected in microfinance)
```

```python
import numpy as np

loans = [5000, 8000, 10000, 12000, 15000, 18000, 22000, 25000, 28000, 120000]

print(f"Min:    ₹{np.min(loans):,}")
print(f"Q1:     ₹{np.percentile(loans, 25):,}")
print(f"Median: ₹{np.median(loans):,}")
print(f"Q3:     ₹{np.percentile(loans, 75):,}")
print(f"Max:    ₹{np.max(loans):,}")

# pandas one-liner
import pandas as pd
df = pd.DataFrame(loans, columns=['Loan Amount'])
print(df.describe())   # gives all 5 + mean + std + count!
```

---

## 7. Box Plot

Visual of the Five-Number Summary — shows **distribution, spread, skewness, and outliers** at one glance.

### Anatomy
```
                   ┌──────────┬──────────┐
   ●         |─────┤   Box    │          ├─────|       ● ●
(outlier)  whisker  Q1       Q2         Q3   whisker (outliers)
                            (Median)

Whiskers extend to last value WITHIN fence (Q1±1.5×IQR)
Points beyond whiskers = outliers (plotted individually)
```

### How to Read a Box Plot

| What you see | What it means |
|--------------|---------------|
| Median line centered | Symmetric distribution |
| Median line near Q1 | Right-skewed |
| Median line near Q3 | Left-skewed |
| Long right whisker | Possible high-end extreme values |
| Dots outside whiskers | Confirmed outliers |
| Short box (small IQR) | Data is concentrated / consistent |
| Wide box (large IQR) | Data is variable / spread out |

### BFSI Use Case — Branch Comparison
```
Branch Cluster    Min    Q1     Median   Q3     Max
─────────────────────────────────────────────────────
Rural            ₹3K   ₹8K    ₹12K    ₹18K   ₹35K
Urban            ₹10K  ₹25K   ₹40K    ₹65K   ₹2L  ← outlier
Semi-Urban       ₹5K   ₹12K   ₹20K    ₹32K   ₹80K

Insights:
→ Urban has widest box → most variable loan sizes
→ Rural has tightest box → consistent small-ticket lending
→ Urban ₹2L is an outlier (upper fence = ₹65K + 1.5×₹40K = ₹1.25L)
```

```python
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd

data = {
    'Loan': [5000,8000,10000,12000,15000,18000,22000,25000,28000,120000,
             10000,25000,40000,60000,65000,70000,80000,200000,
             5000,8000,12000,20000,25000,32000,80000],
    'Branch': ['Rural']*10 + ['Urban']*8 + ['Semi-Urban']*7
}
df = pd.DataFrame(data)

fig, axes = plt.subplots(1, 2, figsize=(14, 6))

sns.boxplot(data=df, x='Branch', y='Loan', ax=axes[0], palette='Set2')
axes[0].set_title('Loan Amount by Branch Type')
axes[0].set_ylabel('Loan Amount (₹)')

sns.boxplot(y=df['Loan'], ax=axes[1], color='steelblue')
axes[1].set_title('Overall Loan Distribution')

plt.tight_layout()
plt.savefig('boxplot_loans.png', dpi=150)
plt.show()
```

---

## 🎯 Interview Q&A

| Question | Model Answer |
|----------|-------------|
| **Mean vs Median — when to use which?** | Mean for symmetric data without outliers. Median when data is skewed or has outliers. BFSI data (income, loans) = almost always median. |
| **What is Bessel's correction?** | Using (n−1) in sample variance to compensate for the fact that sample deviations from sample mean are smaller than from true population mean. Makes the estimator unbiased. |
| **What are degrees of freedom?** | With n points and a known sample mean, only n−1 values are free to vary. The last is determined. So df = n−1 for variance. |
| **High SD in loan repayment data means?** | Highly inconsistent repayment behavior across customers → higher credit risk → needs deeper segmentation. |
| **How to detect outliers with IQR?** | Calculate IQR = Q3−Q1. Outliers are below Q1−1.5×IQR or above Q3+1.5×IQR. Robust because IQR itself is unaffected by outliers. |
| **Box plot vs Histogram — difference?** | Histogram shows shape/frequency distribution. Box plot shows Q1/Q2/Q3/IQR/outliers explicitly. Box plots are better for comparing multiple groups side by side. |
| **Median near Q1 in box plot means?** | Right-skewed distribution — majority of values are on the lower end, long tail on the right. Typical in loan and income data. |
| **What does `df.describe()` give in pandas?** | Count, mean, std, min, Q1(25%), Q2(50%/median), Q3(75%), max — the full five-number summary plus mean and SD. |

---

## ⚡ Quick Reference Cheat Sheet

```
CENTRAL TENDENCY
─────────────────────────────────────────────
Mean   → μ = Σx/N  |  x̄ = Σx/n       [sensitive to outliers]
Median → Middle value (sorted)          [robust to outliers]
Mode   → Most frequent value            [only option for nominal data]

DISPERSION
─────────────────────────────────────────────
Population Variance:  σ²= Σ(x−μ)²/N
Sample Variance:      s² = Σ(x−x̄)²/(n−1)   ← Bessel's correction
Population SD:        σ  = √σ²
Sample SD:            s  = √s²
(numpy: ddof=0 for population, ddof=1 for sample)

PERCENTILES & QUARTILES
─────────────────────────────────────────────
Q1 = P25  |  Q2 = P50 = Median  |  Q3 = P75
IQR = Q3 − Q1
Outlier fences: Q1−1.5×IQR  and  Q3+1.5×IQR

FIVE-NUMBER SUMMARY
─────────────────────────────────────────────
Min | Q1 | Median | Q3 | Max
pandas: df.describe()
```

---

## 🔗 Connect

- 🐙 GitHub: [@mmtiwari222](https://github.com/mmtiwari222)
- 💼 LinkedIn: Learning in public | IT Analyst → Data Analyst
- 🏢 Domain: BFSI / Microfinance @ Sindhuja Microcredit

---

*Day 2 of Statistics for Data Analysis. Part of my DA → DS → ML → AI learning journey. One topic at a time. 🚀*