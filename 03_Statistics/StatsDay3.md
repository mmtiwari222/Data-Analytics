# 📉 Statistics Day 3 — Normal Distribution, Empirical Rule & Standard Normal

> **Learning Track:** DA → DS → ML → AI | **Date:** July 5, 2026
> **Author:** [@mmtiwari222](https://github.com/mmtiwari222) | Learning in public. Building in public. 🚀

---

## 📌 Topics Covered

| # | Topic |
|---|-------|
| 1 | [Five-Number Summary](#1-five-number-summary) |
| 2 | [Gaussian / Normal Distribution](#2-gaussian--normal-distribution) |
| 3 | [Empirical Rule (68-95-99.7)](#3-empirical-rule-68-95-997-rule) |
| 4 | [Standard Normal Distribution & Z-Score](#4-standard-normal-distribution--z-score) |
| 5 | [Connecting All Concepts](#5-connecting-all-concepts) |
| 6 | [Interview Q&A](#6-interview-qa) |
| 7 | [Quick Reference Cheat Sheet](#7-quick-reference-cheat-sheet) |

---

## 1. Five-Number Summary

The most compact description of any dataset using exactly 5 values.

```
┌─────┬────┬────────┬────┬─────┐
│ Min │ Q1 │ Median │ Q3 │ Max │
└─────┴────┴────────┴────┴─────┘
```

| Statistic | What it tells you |
|-----------|-------------------|
| **Min** | Smallest value in dataset |
| **Q1 (P25)** | 25% of data falls below this |
| **Median (Q2/P50)** | Middle — 50% below, 50% above |
| **Q3 (P75)** | 75% of data falls below this |
| **Max** | Largest value in dataset |

### How to Calculate

```
Step 1: Sort data ascending
Step 2: Find Median (Q2) → splits into lower & upper halves
Step 3: Q1 = Median of the LOWER half
Step 4: Q3 = Median of the UPPER half
Step 5: Min = first value, Max = last value
```

### Worked Example

```
Dataset: 4, 7, 9, 12, 15, 18, 21, 24, 28, 35

Sorted:  4, 7, 9, 12, 15 | 18, 21, 24, 28, 35

Min    = 4
Q1     = Median of [4,7,9,12,15]    = 9
Median = (15 + 18) / 2              = 16.5
Q3     = Median of [18,21,24,28,35] = 24
Max    = 35
IQR    = Q3 − Q1 = 24 − 9          = 15
```

### What Patterns Tell You

| Pattern | Meaning |
|---------|---------|
| Median closer to Q1 | Right-skewed |
| Median closer to Q3 | Left-skewed |
| Median in center | Symmetric |
| Max far from Q3 | High-end outliers possible |
| Min far from Q1 | Low-end outliers possible |
| Large IQR | High variability in middle 50% |
| Small IQR | Data is concentrated / consistent |

> 💡 **Pro Tip:** Five-number summary + IQR gives you a complete picture of any dataset — center, spread, shape, and outliers — without even plotting a chart.

---

## 2. Gaussian / Normal Distribution

A continuous probability distribution that forms a **perfect bell-shaped curve**. Named after mathematician **Carl Friedrich Gauss**.

### Key Properties

| Property | Value |
|----------|-------|
| **Shape** | Symmetric bell curve |
| **Mean = Median = Mode** | All equal, all at center |
| **Skewness** | 0 (perfectly symmetric) |
| **Total area under curve** | = 1 (represents 100% of data) |
| **Tails** | Extend to ±∞, never touch x-axis |

### Bell Curve Shape

```
                    .
                  .   .
                .       .
              .           .
            .               .
──────────.────────────────────────.──────────
     μ−3σ  μ−2σ  μ−σ   μ   μ+σ  μ+2σ  μ+3σ
                        ↑
                  Mean = Median = Mode
```

### The Formula

```
f(x) = (1 / σ√2π) × e^[−(x−μ)² / 2σ²]

μ = mean     → controls CENTER position of the curve
σ = std dev  → controls WIDTH / SPREAD of the curve
π = 3.14159...
e = 2.71828... (Euler's number)
```

> You don't need to memorize this formula for DA interviews — but knowing what μ and σ control is essential.

### What μ and σ Control

| Change | Effect on Curve |
|--------|----------------|
| Increase μ | Curve shifts RIGHT |
| Decrease μ | Curve shifts LEFT |
| Increase σ | Curve gets WIDER and FLATTER |
| Decrease σ | Curve gets NARROWER and TALLER |

### Real-World Examples

| Domain | Example |
|--------|---------|
| HR | Employee performance ratings across large organizations |
| Manufacturing | Product weight/dimensions from a production line |
| Education | Exam scores across large student populations |
| Finance | Daily stock returns (approximately normal) |
| Healthcare | Blood pressure readings in a healthy population |
| Quality Control | Measurement errors in precision instruments |

### Why Normal Distribution Matters for DA/ML

- Many statistical tests **assume normality** (t-test, ANOVA, linear regression residuals)
- **Central Limit Theorem** → sample means tend toward normal regardless of original distribution
- Z-scores and probability lookups require normality assumption
- Foundation for anomaly detection, confidence intervals, hypothesis testing

> 💡 **Interview Tip:** *"I check normality during EDA using histograms and QQ-plots. If data isn't normal, I consider log transformation or switch to non-parametric methods."*

---

## 3. Empirical Rule (68-95-99.7 Rule)

For any **normally distributed** dataset, this rule tells you exactly what percentage of data falls within 1, 2, or 3 standard deviations from the mean.

```
┌─────────────────────────────────────────────┐
│              EMPIRICAL RULE                 │
│                                             │
│  ←──────────── 99.7% ────────────→         │
│       ←────────── 95% ──────────→          │
│            ←───── 68% ─────→               │
│                    │                        │
│  μ−3σ  μ−2σ  μ−σ  μ  μ+σ  μ+2σ  μ+3σ    │
└─────────────────────────────────────────────┘
```

| Range | % of Data | Intuition |
|-------|-----------|-----------|
| μ ± 1σ | **68.27%** | ~2 in every 3 data points |
| μ ± 2σ | **95.45%** | ~19 in every 20 data points |
| μ ± 3σ | **99.73%** | Almost everything |
| Beyond ±3σ | **0.27%** | Extremely rare → flag as outlier |

### Worked Example

```
Scenario: Employee salaries
Mean (μ) = ₹50,000/month
SD   (σ) = ₹8,000/month

68%   → ₹42,000  to  ₹58,000   (μ ± 1σ)
95%   → ₹34,000  to  ₹66,000   (μ ± 2σ)
99.7% → ₹26,000  to  ₹74,000   (μ ± 3σ)

Anyone earning > ₹74K or < ₹26K = statistical outlier
```

### Practical Applications

| Use Case | How Empirical Rule Helps |
|----------|--------------------------|
| **Outlier detection** | Flag anything beyond μ ± 3σ |
| **Quality control** | Set tolerance bands for production |
| **HR analytics** | Define normal performance/salary ranges |
| **Anomaly detection** | Alert when metrics exceed 2σ |
| **Risk management** | Define acceptable deviation limits |

---

## 4. Standard Normal Distribution & Z-Score

### What is Standard Normal Distribution?

A **special case** of normal distribution with:

```
Mean  (μ) = 0
Std Dev (σ) = 1
Symbol: N(0, 1)
```

Every normal distribution can be **converted** to standard normal using the **Z-score formula**.

### Why Do We Need It?

Different datasets have different μ and σ. Standard normal gives a **universal reference scale** to compare any value from any dataset on equal footing.

### Z-Score Formula

```
Z = (x − μ) / σ

x = individual data point
μ = mean of the distribution
σ = standard deviation
Z = number of SDs the value is away from the mean
```

### How to Interpret Z-Scores

| Z-Score | Meaning |
|---------|---------|
| Z = 0 | Value equals the mean |
| Z = +1 | 1 SD above mean |
| Z = −1 | 1 SD below mean |
| Z = +2 | 2 SDs above mean — top ~2.5% |
| Z > +3 | Extreme high outlier |
| Z < −3 | Extreme low outlier |

### Worked Example — Fair Comparison Across Datasets

```
Two candidates, two different tests:

Candidate A: Score = 75,  Test μ = 60, σ = 10
Z_A = (75 − 60) / 10 = +1.5

Candidate B: Score = 82,  Test μ = 75, σ = 15
Z_B = (82 − 75) / 15 = +0.47

→ Candidate A performed BETTER relative to their group
  (1.5 SDs above mean vs only 0.47 SDs above mean)

Raw scores lie. Z-scores tell the truth.
```

### Z-Score for Outlier Detection

```
Rule: |Z| > 3 → potential outlier

Example:
μ = ₹50,000,  σ = ₹8,000
Value = ₹1,00,000

Z = (1,00,000 − 50,000) / 8,000 = 6.25
|Z| = 6.25 > 3 → OUTLIER confirmed
```

### Z-Table — Key Values

| Z-Score | % of Data BELOW this value |
|---------|---------------------------|
| Z = −2.0 | 2.28% |
| Z = −1.0 | 15.87% |
| Z = 0.0 | 50.00% |
| Z = +1.0 | 84.13% |
| Z = +2.0 | 97.72% |
| Z = +3.0 | 99.87% |

### Normal vs Standard Normal — Side by Side

| Property | Normal Distribution | Standard Normal |
|----------|--------------------|-----------------| 
| Mean | Any μ | 0 |
| Std Dev | Any σ | 1 |
| Symbol | N(μ, σ²) | N(0, 1) |
| Use | Describe real data | Compare & probability lookup |

---

## 5. Connecting All Concepts

```
Real Dataset
     ↓
Plot Histogram → Check shape
     ↓
Bell-shaped? → Normal Distribution N(μ, σ²)
     ↓
Calculate μ and σ
     ↓
Apply Empirical Rule → 68% / 95% / 99.7% ranges
     ↓
Convert to Z-score → Standard Normal N(0,1)
     ↓
Use Z-table → Find probabilities
     ↓
Flag |Z| > 3 → Outlier detection
     ↓
Five-Number Summary + Box Plot → Visual confirmation
```

---

## 6. Interview Q&A

| Question | Model Answer |
|----------|-------------|
| **Normal vs Standard Normal?** | Normal has any μ and σ. Standard normal is a special case with μ=0, σ=1. Any normal distribution can be converted using Z = (x−μ)/σ. |
| **What does the empirical rule state?** | 68% within 1σ, 95% within 2σ, 99.7% within 3σ. Used to quickly set outlier thresholds and quality control bands. |
| **What is a Z-score?** | Number of standard deviations a value is from the mean. Z = (x−μ)/σ. Used for outlier detection and cross-dataset comparison. |
| **How do you check normality in data?** | Histogram (visual bell shape), QQ-plot (points follow diagonal line), Shapiro-Wilk test (p > 0.05 = normal). |
| **What is the Central Limit Theorem?** | Even if the population is not normal, the distribution of sample means approaches normal as sample size increases (n ≥ 30). This is why normal distribution is so powerful. |
| **Five-number summary vs box plot?** | Five-number summary is the data (Min, Q1, Median, Q3, Max). Box plot is the visual representation of it. |
| **When is median better than mean?** | When data is skewed or has outliers. Median is not affected by extreme values. |

---

## 7. Quick Reference Cheat Sheet

```
FIVE-NUMBER SUMMARY
────────────────────────────────────
Min | Q1 | Median | Q3 | Max
IQR = Q3 − Q1
Outlier: below Q1−1.5×IQR  or  above Q3+1.5×IQR

NORMAL DISTRIBUTION
────────────────────────────────────
Symbol:     N(μ, σ²)
Properties: Symmetric, Mean = Median = Mode, Area = 1
μ → shifts center  |  σ → controls width

EMPIRICAL RULE
────────────────────────────────────
μ ± 1σ  →  68.27% of data
μ ± 2σ  →  95.45% of data
μ ± 3σ  →  99.73% of data
Beyond ±3σ → Outlier zone (0.27%)

STANDARD NORMAL & Z-SCORE
────────────────────────────────────
Z = (x − μ) / σ
N(0, 1): Mean = 0, SD = 1
|Z| > 3  →  Outlier
Z-table  →  gives probability (area under curve)
```

---

## 🔗 Connect

- 🐙 GitHub: [@mmtiwari222](https://github.com/mmtiwari222)
- 💼 LinkedIn: Learning in public | Aspiring Data Analyst
- 📓 Full notes with examples → Notion

---

*Day 3 of Statistics for Data Analysis. Part of my DA → DS → ML → AI learning journey. One concept at a time. 🚀*
