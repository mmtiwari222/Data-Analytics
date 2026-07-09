# 📊 Statistics Day 7 — Chi-Square, ANOVA, Distributions, Outliers, Binomial & Two-Proportion Z-Test

> **Learning Track:** DA → DS → ML → AI | **Date:** July 9, 2026
> **Author:** [@mmtiwari222](https://github.com/mmtiwari222) | Learning in public. Building in public. 🚀

---

## 📌 Topics Covered

| # | Topic |
|---|-------|
| 1 | [Chi-Square Test](#1-chi-square-test-χ²-test) |
| 2 | [ANOVA & F-Test](#2-anova-analysis-of-variance) |
| 3 | [Confidence Interval Revision](#3-confidence-interval--revision) |
| 4 | [Pearson vs Spearman Revision](#4-pearson-vs-spearman--revision) |
| 5 | [Pareto Distribution](#5-pareto-distribution-8020-rule) |
| 6 | [Power Law Distribution](#6-power-law-distribution) |
| 7 | [Log-Normal Distribution](#7-log-normal-distribution) |
| 8 | [Box-Cox Transformation](#8-box-cox-transformation) |
| 9 | [Missing Values & Mean Imputation](#9-missing-values) |
| 10 | [Outlier Detection](#10-outlier-detection) |
| 11 | [Why (n−1) in Sample Variance](#11-why-sample-variance-uses-n1) |
| 12 | [P-Value Revision](#12-p-value--revision) |
| 13 | [T-Test vs Z-Test Revision](#13-t-test-vs-z-test--revision) |
| 14 | [Bernoulli Distribution](#14-bernoulli-distribution) |
| 15 | [Binomial Distribution](#15-binomial-distribution) |
| 16 | [Two-Proportion Z-Test](#16-z-test-for-two-population-proportions) |
| 17 | [Interview Q&A](#17-interview-qa) |
| 18 | [Quick Reference](#18-quick-reference-cheat-sheet) |

---

## 1. Chi-Square Test (χ² Test)

### Introduction

Non-parametric test for **categorical data**. Tests association or distribution fit.

```
Non-parametric = does NOT assume normal distribution
Categorical    = data in groups/labels (not continuous numbers)
```

### Two Types

| Type | Question | Example |
|------|---------|---------|
| **Goodness of Fit** | Does sample match expected distribution? | Is a dice fair? |
| **Test of Independence** | Are two categorical variables related? | Gender vs product preference? |

### Formula

```
χ² = Σ [(O − E)² / E]

O = Observed frequency (actual data)
E = Expected frequency (if H₀ were true)
```

### Expected Frequency

```
Goodness of Fit:      E = n × p₀
Test of Independence: E = (Row Total × Column Total) / Grand Total
```

### Degrees of Freedom

```
Goodness of Fit:      df = k − 1         (k = number of categories)
Test of Independence: df = (r−1)(c−1)    (r = rows, c = columns)
```

### Decision Rule

```
χ² calculated > χ² critical  →  REJECT H₀
p-value < α                  →  REJECT H₀

χ² is always ≥ 0 (squaring removes negatives)
Higher χ² = more difference between observed and expected
```

---

### Goodness of Fit — Worked Example

```
Problem: Is a dice fair? Rolled 60 times. Expected: 10 per face.

Face   Observed(O)  Expected(E)  (O−E)²/E
1          8           10          0.40
2         12           10          0.40
3         10           10          0.00
4          9           10          0.10
5         13           10          0.90
6          8           10          0.40
                                ─────────
χ² = 2.20

df = 6 − 1 = 5
χ² critical (df=5, α=0.05) = 11.07

2.20 < 11.07  →  FAIL TO REJECT H₀
Conclusion: No evidence dice is unfair
```

---

### Test of Independence — Worked Example

```
Problem: Is gender related to product preference?

Observed:
             Product A   Product B   Total
Male            30          20         50
Female          20          30         50
Total           50          50        100

Expected (E = Row × Col / Grand Total):
             Product A   Product B
Male            25          25
Female          25          25

χ² = (30−25)²/25 + (20−25)²/25 + (20−25)²/25 + (30−25)²/25
   = 1 + 1 + 1 + 1 = 4.0

df = (2−1)(2−1) = 1
χ² critical (df=1, α=0.05) = 3.841

4.0 > 3.841  →  REJECT H₀
Conclusion: Gender and product preference ARE associated
```

> 💡 **Interview Tip:** *"I use Chi-Square for feature selection in classification problems — testing which categorical features are significantly associated with the categorical target variable."*

---

## 2. ANOVA (Analysis of Variance)

### What is ANOVA?

Tests whether **means of 3 or more groups** are significantly different.

```
Why not multiple t-tests?
→ 3 groups = 3 t-tests → combined Type I error ≈ 14% (not 5%)
→ ANOVA tests all simultaneously at α = 0.05
```

### F-Test

```
F = Variance BETWEEN groups / Variance WITHIN groups
  = MSB / MSW

F >> 1  →  Between-group variation large → groups differ → Reject H₀
F ≈ 1   →  No significant difference → Fail to Reject H₀
```

### Hypotheses

```
H₀: μ₁ = μ₂ = μ₃ = ... = μₖ   (all group means equal)
H₁: At least one group mean is different
```

### Real Example

```
Compare test scores across 3 teaching methods:
Method A: 75, 80, 78
Method B: 85, 88, 82
Method C: 70, 72, 68

ANOVA answers: Are these differences real or just random noise?
```

> 💡 **Interview Tip:** *"ANOVA tells you IF groups differ, not WHICH ones. For that, use post-hoc tests like Tukey's HSD."*

---

## 3. Confidence Interval — Revision

```
CI = x̄ ± Z* × (σ/√n)    [σ known]
CI = x̄ ± t* × (s/√n)    [σ unknown]

90% CI  →  Z* = 1.645
95% CI  →  Z* = 1.960
99% CI  →  Z* = 2.576

Key rules:
→ CI gives a RANGE, not a point
→ Larger n → narrower CI (more precise)
→ Higher confidence → wider CI
→ "95% confident" = 95 of 100 such CIs contain true μ
→ NEVER say "95% probability μ is in this interval" (μ is fixed)
```

---

## 4. Pearson vs Spearman — Revision

```
Pearson:  r = Cov(X,Y) / (σₓ × σᵧ)
→ Linear relationships, continuous normal data, sensitive to outliers

Spearman: rₛ = 1 − 6Σd²/n(n²−1)
→ Rank-based, monotonic, robust to outliers, works for ordinal data

Use Pearson: Normal + Linear + Clean data
Use Spearman: Skewed / Ordinal / Outliers present / Non-linear monotonic
```

---

## 5. Pareto Distribution (80–20 Rule)

### The Rule

```
80% of effects come from 20% of causes
```

### Real Examples

| Domain | 80% of... | From 20% of... |
|--------|-----------|----------------|
| E-commerce | Revenue | Products |
| Banking | Profits | Customers |
| Software | Crashes | Bug types |
| HR | Productivity | Employees |
| Support | Tickets | Issue categories |

### Properties

```
Right-skewed (heavy right tail)
A few items drive most of the impact
Most items have small values
Non-normal distribution
```

### In Data Analysis

```
Pareto Chart = Descending bar chart + Cumulative % line
Used for: Prioritization, Root Cause Analysis, Feature Importance

Example: Which product categories generate 80% of returns?
→ Sort by return count descending
→ Find where cumulative % crosses 80%
→ Fix those categories first
```

---

## 6. Power Law Distribution

### What is it?

A small number of events are extremely common; most events are extremely rare.

```
P(x) ∝ x^(−α)    (scale-free)
```

### Examples

```
City populations    → Few mega-cities, many small towns
Social media        → Few accounts with millions of followers
Website traffic     → Few sites dominate (Google, YouTube)
Wealth distribution → Few billionaires, most earn average
Word frequency      → Few words used constantly
Earthquake sizes    → Few massive, many tiny
```

### Power Law vs Normal

```
Normal:    Bell-shaped, mean = center, outliers are rare exceptions
Power Law: Extreme right skew, no meaningful average,
           "extreme" values are expected and common
```

> 💡 Power Law is why mean fails to describe income or wealth distribution.

---

## 7. Log-Normal Distribution

### What is it?

If log(X) is normally distributed → X follows a Log-Normal distribution.

```
Y = log(X) ~ Normal
→ X ~ Log-Normal
```

### Properties

```
Always right-skewed
All values positive (X > 0)
Mean > Median > Mode
Generated by multiplicative processes
```

### Real Examples

```
Salary / income data
Stock prices and returns
Product lifetimes
Biological measurements (tree heights, bacteria growth)
Loan amounts
City sizes
```

### Why It Matters for DA

```
If your data is log-normally distributed:
→ Take log transform → data becomes approximately normal
→ Apply all normal-based statistical tests
→ After analysis, exponentiate back → original scale

log(X) → analyze → exp(result) = answer in original units
```

---

## 8. Box-Cox Transformation

### What is it?

A family of power transformations that converts **skewed → approximately normal**.

```
y(λ) = (Xλ − 1) / λ    if λ ≠ 0
y(λ) = log(X)           if λ = 0

λ (lambda) = transformation parameter, found by optimization
```

### Common λ Values

| λ | Transformation |
|---|----------------|
| 1 | No change (original) |
| 0 | Log transformation |
| 0.5 | Square root |
| −1 | Inverse (1/X) |
| 2 | Square |

### When to Use

```
Right-skewed data → Box-Cox → closer to normal
ML model assumes normality → transform → model → back-transform
Regression residuals are skewed → apply Box-Cox to target
```

### Process

```
Step 1: Check skewness (histogram, skewness statistic)
Step 2: Apply Box-Cox → algorithm finds best λ
Step 3: Verify transformed data ≈ normal
Step 4: Build model on transformed data
Step 5: Back-transform predictions to original scale
```

> ⚠️ Box-Cox requires all values > 0. If data has zeros/negatives → use **Yeo-Johnson** instead.

---

## 9. Missing Values

### Types of Missing Data

```
MCAR: Missing Completely At Random  → no pattern (safe to drop)
MAR:  Missing At Random             → depends on other observed variables
MNAR: Missing Not At Random         → depends on the missing value itself
```

### Disadvantages of Mean Imputation

```
Problem 1: Reduces variance
→ Replacing with mean pulls values toward center
→ Artificially decreases spread and SD

Problem 2: Distorts distribution
→ Creates spike at mean
→ Especially bad for skewed distributions

Problem 3: Breaks inter-variable relationships
→ Imputed values don't preserve correlations between features

Problem 4: Hides missingness patterns
→ If values are MNAR, the reason for missingness is informative
→ Mean imputation erases that signal
```

### Better Alternatives

| Method | When to Use |
|--------|------------|
| **Median imputation** | Skewed data, outliers present |
| **Mode imputation** | Categorical variables |
| **KNN imputation** | When relationships between features exist |
| **Regression imputation** | When missing values can be predicted |
| **Multiple imputation** | When accuracy is critical |
| **Drop rows/columns** | >50% missing, no recovery possible |

> 💡 **Interview Tip:** *"I never use mean imputation blindly. I check distribution and missingness pattern first. Skewed → median. Categorical → mode. Structured missing → KNN or regression."*

---

## 10. Outlier Detection

### Method 1 — IQR (Five-Number Summary)

```
IQR = Q3 − Q1

Lower fence = Q1 − 1.5 × IQR
Upper fence = Q3 + 1.5 × IQR

Below lower fence → outlier
Above upper fence → outlier

✅ Robust — IQR itself not affected by outliers
✅ Best for skewed data
```

### Method 2 — Box Plot

```
Points beyond whiskers = outliers (visually confirmed)
Whiskers → last value within fence
Dots outside → individual outlier points

✅ Best for quick visual EDA and group comparisons
```

### Method 3 — Z-Score

```
Z = (x − μ) / σ
|Z| > 3  →  outlier

✅ Works well for normally distributed data
❌ Sensitive — mean and SD themselves get pulled by outliers
```

### Comparison

| Method | Based on | Robust? | Best for |
|--------|---------|---------|----------|
| IQR | Quartiles | ✅ Yes | Skewed data |
| Box Plot | IQR (visual) | ✅ Yes | EDA |
| Z-Score | Mean & SD | ❌ No | Normal data |

> 💡 **Interview Tip:** *"I default to IQR — it's robust. Z-score only when data is confirmed normal. Always visualize with box plot before treatment."*

---

## 11. Why Sample Variance Uses (n−1)

### The Problem

```
s² = Σ(xᵢ − x̄)² / n  →  UNDERESTIMATES σ²

Why?
Sample values cluster closer to SAMPLE mean (x̄)
than to TRUE population mean (μ)
→ Σ(xᵢ − x̄)² is always smaller than Σ(xᵢ − μ)²
→ Dividing by n gives a biased (too small) estimate
```

### Degrees of Freedom

```
n data points collected
1 parameter estimated (x̄) from them

Once x̄ and (n−1) values are known → nth value is fixed
→ Only (n−1) values are truly free = degrees of freedom

Example:
4 values with x̄ = 5:  2, 4, 6, ?
? MUST be 8 → not free
→ df = 3 = n − 1
```

### Result

```
Biased:   s² = Σ(xᵢ−x̄)² / n      →  E[s²] < σ² (wrong)
Unbiased: s² = Σ(xᵢ−x̄)² / (n−1)  →  E[s²] = σ² (correct on average)

Bessel's Correction = dividing by (n−1) instead of n
```

---

## 12. P-Value — Revision

```
P-value = P(result this extreme OR more | H₀ is true)

p < α   →  Reject H₀
p ≥ α   →  Fail to Reject H₀
NEVER "Accept H₀"

Thresholds:
p < 0.01  →  Very strong evidence
p < 0.05  →  Strong evidence (standard)
p < 0.10  →  Weak evidence
p > 0.10  →  Insufficient evidence
```

---

## 13. T-Test vs Z-Test — Revision

```
Z-TEST:   σ known OR n ≥ 30
          Z = (x̄ − μ₀) / (σ/√n)
          Uses Z-table

T-TEST:   σ unknown, especially n < 30
          t = (x̄ − μ₀) / (s/√n),  df = n−1
          Uses t-table (fatter tails)
          As n → large, t → Z
```

---

## 14. Bernoulli Distribution

```
Single trial, exactly two outcomes: Success (1) or Failure (0)

P(X=1) = p
P(X=0) = 1 − p

Mean     = p
Variance = p(1−p)

Examples:
→ Coin toss: p = 0.5
→ Email click: p = 0.03
→ Product defect: p = 0.02

Bernoulli = 1 trial
Binomial  = n repeated Bernoulli trials
```

---

## 15. Binomial Distribution

### What is it?

Number of **successes in n independent Bernoulli trials**.

```
Conditions:
1. Fixed n trials
2. Only 2 outcomes per trial
3. Constant probability p
4. Independent trials
```

### Formula

```
P(X = k) = ⁿCₖ × pᵏ × (1−p)^(n−k)

k = number of successes
n = total trials
p = P(success) per trial

Mean     = n × p
Variance = n × p × (1−p)
SD       = √[n × p × (1−p)]
```

### Worked Example

```
Call center: 10% conversion rate per call
8 calls made. P(exactly 3 conversions)?

n=8, k=3, p=0.10

P(X=3) = ⁸C₃ × (0.10)³ × (0.90)⁵
        = 56 × 0.001 × 0.59049
        = 0.0331 = 3.31%
```

### Bernoulli vs Binomial

| Feature | Bernoulli | Binomial |
|---------|-----------|----------|
| Trials | 1 | n |
| Outcomes | 2 | 0 to n successes |
| Mean | p | np |
| Variance | p(1−p) | np(1−p) |

### Normal Approximation

```
When np ≥ 5 AND n(1−p) ≥ 5:
Binomial ≈ Normal → N(μ=np, σ²=np(1−p))
→ Can use Z-test on large binomial problems
```

---

## 16. Z-Test for Two Population Proportions

### What is it?

Tests whether **two population proportions are significantly different**.

```
H₀: p₁ = p₂
H₁: p₁ ≠ p₂  (two-tailed)  OR
    p₁ > p₂  (right-tailed) OR
    p₁ < p₂  (left-tailed)
```

### Formula

```
Pooled proportion:
p̂c = (x₁ + x₂) / (n₁ + n₂)

Standard Error:
SE = √[p̂c(1−p̂c) × (1/n₁ + 1/n₂)]

Test Statistic:
Z = (p̂₁ − p̂₂) / SE
```

### Why Pooled Proportion?

```
Under H₀, we ASSUME p₁ = p₂
→ Best estimate of this common p = combine both samples
→ p̂c = (x₁ + x₂) / (n₁ + n₂)
```

---

### Example 1 — Vaccine Trial

```
Group 1 (Vaccine): n₁=500, 45 sick  → p̂₁ = 0.090
Group 2 (Placebo): n₂=500, 90 sick  → p̂₂ = 0.180
α = 0.05

H₀: p₁ = p₂
H₁: p₁ < p₂   (left-tailed — vaccine should reduce illness)

p̂c = (45+90)/(500+500) = 135/1000 = 0.135

SE = √[0.135 × 0.865 × (1/500 + 1/500)]
   = √[0.116775 × 0.004]
   = √0.000467
   = 0.02161

Z = (0.090 − 0.180) / 0.02161 = −4.16

Critical Z (left, α=0.05) = −1.645
−4.16 < −1.645  →  REJECT H₀

✅ Conclusion: Vaccine significantly reduces illness rate
```

---

### Example 2 — Ad Campaign Comparison

```
Campaign A: n₁=300, 72 clicks  → p̂₁ = 0.24
Campaign B: n₂=400, 80 clicks  → p̂₂ = 0.20
α = 0.05

H₀: p₁ = p₂
H₁: p₁ ≠ p₂   (two-tailed)

p̂c = (72+80)/(300+400) = 152/700 = 0.2171

SE = √[0.2171 × 0.7829 × (1/300 + 1/400)]
   = √[0.1700 × 0.00583]
   = √0.000991
   = 0.0315

Z = (0.24 − 0.20) / 0.0315 = 1.27

Critical Z (two-tailed, α=0.05) = ±1.96
|Z| = 1.27 < 1.96  →  FAIL TO REJECT H₀

✅ Conclusion: No significant difference in click rates
```

---

## 17. Interview Q&A

| Question | Model Answer |
|----------|-------------|
| **Goodness of Fit vs Test of Independence?** | GoF: single variable vs expected distribution, df=k−1. Independence: two categorical variables, df=(r−1)(c−1). Different questions, different setups. |
| **Why ANOVA instead of multiple t-tests?** | Multiple t-tests inflate Type I error. 3 groups = 3 tests ≈ 14% error rate. ANOVA controls it at α=0.05 simultaneously. |
| **Disadvantage of mean imputation?** | Reduces variance, distorts distribution, breaks inter-variable correlations, hides MNAR patterns. Use median/KNN/regression instead. |
| **What is Box-Cox used for?** | Transforms skewed data to approximately normal using power transformation. Algorithm finds optimal λ. Requires all values > 0. |
| **Bernoulli vs Binomial?** | Bernoulli = 1 trial, 2 outcomes. Binomial = n independent Bernoulli trials, counts successes. Mean: p vs np. Variance: p(1−p) vs np(1−p). |
| **When to use two-proportion Z-test?** | Comparing proportions from two independent groups. A/B testing, clinical trials, survey comparisons. Uses pooled proportion because H₀ assumes both are equal. |
| **What is Power Law distribution?** | Scale-free distribution where few items dominate. Examples: wealth, followers, traffic. Cannot use mean. |
| **IQR vs Z-score for outliers?** | IQR is robust (quartiles not affected by outliers). Z-score assumes normality and is sensitive to extreme values. Default to IQR. |
| **What is log-normal distribution?** | log(X) is normally distributed. Always positive, right-skewed. Common in income, stock prices, loan amounts. Log transform → normalize → analyze. |

---

## 18. Quick Reference Cheat Sheet

```
CHI-SQUARE
──────────────────────────────────────────────────
χ² = Σ[(O−E)²/E]
GoF: df = k−1  |  Independence: df = (r−1)(c−1)
E (GoF) = n×p₀  |  E (Indep) = RowTotal×ColTotal/GrandTotal
χ²calc > χ²critical  →  Reject H₀

ANOVA
──────────────────────────────────────────────────
F = MSB / MSW  (Between / Within variance)
F >> 1 → Reject H₀ | H₀: all means equal

DISTRIBUTIONS
──────────────────────────────────────────────────
Pareto:    80-20 rule, right-skewed
Power Law: Extreme right skew, scale-free, X^(−α)
Log-Normal: log(X)~Normal, always positive, right-skewed
Box-Cox:   Skewed→Normal, finds optimal λ, needs X>0

BINOMIAL
──────────────────────────────────────────────────
P(X=k) = ⁿCₖ × pᵏ × (1−p)^(n−k)
Mean = np  |  Variance = np(1−p)
Normal approx: np≥5 AND n(1−p)≥5

TWO-PROPORTION Z-TEST
──────────────────────────────────────────────────
p̂c = (x₁+x₂)/(n₁+n₂)
SE = √[p̂c(1−p̂c)(1/n₁+1/n₂)]
Z  = (p̂₁−p̂₂)/SE

OUTLIER DETECTION
──────────────────────────────────────────────────
IQR:     Fences = Q1±1.5×IQR  (robust, default)
Z-Score: |Z|>3 → outlier  (normal data only)

SAMPLE VARIANCE
──────────────────────────────────────────────────
s² = Σ(xᵢ−x̄)²/(n−1)  →  Bessel's correction
df = n−1 (1 lost estimating x̄)
```

---

## 🔗 Connect

- 🐙 GitHub: [@mmtiwari222](https://github.com/mmtiwari222)
- 💼 LinkedIn: Learning in public | Aspiring Data Analyst
- 📓 Full notes → Notion

---

*Day 7 of Statistics for Data Analysis. Part of my DA → DS → ML → AI learning journey. 🚀*
