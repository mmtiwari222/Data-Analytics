# 📊 Statistics Day 5 — Correlation, Inferential Stats, Hypothesis Testing, CI, Z-Test & T-Test

> **Learning Track:** DA → DS → ML → AI | **Date:** July 7, 2026
> **Author:** [@mmtiwari222](https://github.com/mmtiwari222) | Learning in public. Building in public. 🚀

---

## 📌 Topics Covered

| # | Topic |
|---|-------|
| 1 | [Correlation — Complete](#1-correlation--complete) |
| 2 | [Inferential Statistics](#2-inferential-statistics) |
| 3 | [P-Value](#3-p-value) |
| 4 | [Hypothesis Testing](#4-hypothesis-testing) |
| 5 | [Significance Level (α)](#5-significance-level-α) |
| 6 | [Confidence Interval](#6-confidence-interval) |
| 7 | [Point Estimate](#7-point-estimate) |
| 8 | [Z-Test](#8-z-test) |
| 9 | [t-Test](#9-t-test) |
| 10 | [One-Tailed vs Two-Tailed](#10-one-tailed-vs-two-tailed-test) |
| 11 | [Practical Examples](#11-practical-examples) |
| 12 | [Interview Q&A](#12-interview-qa) |
| 13 | [Quick Reference](#13-quick-reference-cheat-sheet) |

---

## 1. Correlation — Complete

### Covariance Revision

```
Sample Cov(X,Y) = Σ[(xᵢ − x̄)(yᵢ − ȳ)] / (n−1)

Cov > 0 → same direction
Cov < 0 → opposite direction
Cov = 0 → no linear relationship
Problem: value is unit-dependent → can't compare across datasets
```

---

### Pearson Correlation Coefficient

Normalizes covariance to a −1 to +1 scale.

```
r = Cov(X,Y) / (σₓ × σᵧ)

OR expanded:
r = Σ[(xᵢ−x̄)(yᵢ−ȳ)] / √[Σ(xᵢ−x̄)² × Σ(yᵢ−ȳ)²]
```

- Measures **linear** relationships only
- Sensitive to outliers
- Requires continuous, normally distributed data

---

### Spearman Rank Correlation

```
rₛ = 1 − [6 × Σd²] / [n(n²−1)]

d = difference in ranks for each pair
n = number of observations
```

**Worked Example:**

```
Student  Hours(X)  Rank_X  Score(Y)  Rank_Y   d    d²
A           2         1       50        1      0     0
B           4         2       65        3     −1     1
C           6         3       60        2     +1     1
D           8         4       85        4      0     0

Σd² = 2,  n = 4

rₛ = 1 − [6×2] / [4(16−1)]
   = 1 − 12/60
   = 0.80  → Strong positive rank correlation
```

---

### Pearson vs Spearman

| Feature | Pearson | Spearman |
|---------|---------|----------|
| Data type | Continuous, normal | Ordinal or any |
| Relationship | Linear only | Monotonic |
| Outlier sensitivity | High ✗ | Low ✓ (robust) |
| Based on | Raw values | Ranks |
| Formula | Cov/σₓσᵧ | 1 − 6Σd²/n(n²−1) |
| Use when | Clean, normal data | Skewed, ordinal, outliers |

---

### Correlation Range (−1 to +1)

```
−1.0 ──────────── 0.0 ──────────── +1.0
  ↑                 ↑                 ↑
Perfect          No linear          Perfect
Negative         relationship       Positive
```

| Range | Interpretation |
|-------|----------------|
| ±0.9 – ±1.0 | Very strong |
| ±0.7 – ±0.9 | Strong |
| ±0.5 – ±0.7 | Moderate |
| ±0.3 – ±0.5 | Weak |
| 0.0 – ±0.3 | Very weak / negligible |

---

### Positive, Negative & Zero Correlation

**Positive:** Both variables increase together
→ Study hours & exam score, Experience & salary

**Negative:** One increases, other decreases
→ Price & demand, Sleep deprivation & productivity

**Zero:** No linear relationship
→ Shoe size & salary, Name length & IQ

> ⚠️ Zero correlation ≠ no relationship. Two variables can have a strong **non-linear** relationship with r = 0. Always plot a scatter plot first.

---

### Linear vs Non-Linear Data

| Relationship | Pearson | Spearman |
|--------------|---------|----------|
| Linear | ✅ Works | ✅ Works |
| Non-linear monotonic | ❌ Misleading | ✅ Works |
| Non-monotonic (U-shape) | ❌ Fails | ❌ Fails |

---

### Feature Selection Using Correlation

**1. Remove Multicollinearity**
```
If Feature A and Feature B have |r| > 0.85
→ They carry redundant information
→ Drop one of them before modeling
```

**2. Find Relevant Features**
```
Correlate each feature with the target variable
Keep features with |r| > 0.3 (threshold varies by domain)
Drop features with near-zero correlation to target
```

**3. Correlation Heatmap**
```
Visual matrix of all feature relationships
Warm colors = high positive correlation
Cool colors = high negative correlation
Near white = no correlation
→ Most efficient way to spot multicollinearity at a glance
```

> 💡 **Interview Answer:** *"I use a correlation matrix during EDA for feature selection. Features with |r| > 0.85 with each other are multicollinearity candidates — drop one. Features with near-zero correlation to the target are dropped early."*

---

## 2. Inferential Statistics

### What is Inferential Statistics?

Uses probability and sample data to:
- Estimate population parameters
- Test hypotheses about the population
- Make predictions and draw conclusions beyond observed data

```
Population → Everyone/Everything you want to study
Sample     → Subset you actually collect and analyze

Goal: Use SAMPLE statistics → Draw conclusions about POPULATION
```

| Term | Population | Sample |
|------|-----------|--------|
| Mean | μ | x̄ |
| Std Dev | σ | s |
| Size | N | n |
| Proportion | P | p̂ |

### Two Main Tools

```
1. Estimation       → Confidence Intervals (what IS the true value?)
2. Hypothesis Test  → Is our assumption about the population correct?
```

### Real Example

```
Survey 500 employees → 72% satisfied
→ Infer: ~72% of ALL employees likely satisfied
→ How confident? → Confidence Interval
→ Different from last year's 65%? → Hypothesis Test
```

---

## 3. P-Value

### What is a P-Value?

Probability of obtaining results **at least as extreme** as observed, **assuming H₀ is true**.

```
p-value = P(observed result OR more extreme | H₀ is true)

Small p-value → result is UNLIKELY under H₀ → REJECT H₀
Large p-value → result is LIKELY under H₀  → FAIL TO REJECT H₀
```

### Interpretation

| P-Value | Interpretation |
|---------|----------------|
| p < 0.01 | Very strong evidence → Reject H₀ |
| p < 0.05 | Strong evidence → Reject H₀ |
| p = 0.05 | Borderline — check α |
| p > 0.05 | Weak evidence → Fail to reject H₀ |
| p > 0.10 | Very weak evidence → Definitely fail to reject |

### Decision Rule

```
p-value < α  →  Reject H₀
p-value ≥ α  →  Fail to Reject H₀
```

> 💡 We NEVER "accept" H₀. We either reject it or **fail to reject** it.

---

## 4. Hypothesis Testing

### What is it?

Formal method to decide whether sample evidence supports or contradicts a claim about a population.

### Null Hypothesis (H₀)

- Default assumption — status quo, no effect, no difference
- What we assume true BEFORE collecting evidence
- We try to **disprove** it

```
Examples:
H₀: Coin is fair → P(Heads) = 0.5
H₀: New drug has no effect
H₀: Average salary = ₹50,000
H₀: Placement rate = 85%
```

### Alternative Hypothesis (H₁)

- What we want to prove
- Accepted only when H₀ is rejected

```
H₁: Coin is biased → P(Heads) ≠ 0.5
H₁: Drug has an effect
H₁: Average salary ≠ ₹50,000
H₁: Placement rate ≠ 85%
```

### Steps of Hypothesis Testing

```
Step 1: State H₀ and H₁
Step 2: Choose significance level α (usually 0.05)
Step 3: Select test (Z-test, t-test, chi-square...)
Step 4: Calculate test statistic
Step 5: Find p-value or critical value
Step 6: Compare p-value with α
Step 7: Reject or Fail to Reject H₀ → Interpret in context
```

### Coin Toss Example

```
Test: Toss coin 100 times → Get 65 Heads

H₀: P(Heads) = 0.5  (fair coin)
H₁: P(Heads) ≠ 0.5  (biased)
α  = 0.05

Calculate Z → find p-value → compare with 0.05
If p < 0.05 → Reject H₀ → coin is likely biased
If p > 0.05 → Fail to reject → not enough evidence of bias
```

### Accept vs Reject

| Decision | Meaning |
|----------|---------|
| **Reject H₀** | Strong evidence against null → H₁ supported |
| **Fail to Reject H₀** | Not enough evidence → stay with status quo |
| ❌ Never "Accept H₀" | Absence of evidence ≠ evidence of absence |

---

## 5. Significance Level (α)

### What is α?

Threshold set **before** the test. Defines how extreme results must be to reject H₀.

```
Most common: α = 0.05

Meaning: We accept 5% risk of wrongly rejecting a TRUE H₀
         (This wrong rejection = Type I Error)
```

### Confidence Level & Significance Level

```
Confidence Level = 1 − α

α = 0.05  →  95% Confidence
α = 0.01  →  99% Confidence
α = 0.10  →  90% Confidence
```

| α | Confidence Level | Typical Use |
|---|-----------------|-------------|
| 0.10 | 90% | Less strict / exploratory |
| 0.05 | 95% | Standard — most common |
| 0.01 | 99% | Medical, legal, critical decisions |

---

## 6. Confidence Interval

### What is a Confidence Interval?

A **range** within which we are X% confident the **true population parameter** lies.

```
CI = Point Estimate ± Margin of Error
   = x̄ ± (Z* × σ/√n)

Lower Limit = x̄ − (Z* × σ/√n)
Upper Limit = x̄ + (Z* × σ/√n)
```

### Key Components

| Term | Meaning |
|------|---------|
| **Point Estimate** | Single best guess — x̄ |
| **Margin of Error** | ± buffer = Z* × SE |
| **Standard Error** | SE = σ/√n |
| **Z*** | Critical value for chosen confidence level |

### Critical Z* Values

```
90% CI  →  Z* = 1.645
95% CI  →  Z* = 1.960
99% CI  →  Z* = 2.576
```

### CAT Exam Example

```
Sample: 64 students, x̄ = 120, σ = 16 (known), 95% CI

SE = 16/√64 = 16/8 = 2
Margin of Error = 1.96 × 2 = 3.92

CI = [120 − 3.92,  120 + 3.92]
   = [116.08,  123.92]

Answer: 95% confident true avg CAT score is between 116 and 124
```

### What "95% Confident" Actually Means

```
NOT: "There's 95% probability μ is in this interval"

YES: "If we repeated sampling 100 times and built 100 CIs,
      approximately 95 of them would contain the true μ"
```

### Factors Affecting CI Width

| Factor | Effect on Width |
|--------|----------------|
| ↑ Confidence level | Wider |
| ↑ Sample size (n) | Narrower |
| ↑ Variability (σ) | Wider |

---

## 7. Point Estimate

### What is a Point Estimate?

Single value used to estimate an unknown population parameter.

```
x̄  →  estimates  μ  (population mean)
s   →  estimates  σ  (population std dev)
p̂  →  estimates  P  (population proportion)
```

### Point Estimate vs Confidence Interval

```
Point Estimate:     x̄ = ₹52,000          (single number — false precision)
Confidence Interval: [₹50,432 – ₹53,568]  (range — acknowledges uncertainty)

CI is ALWAYS more informative than a point estimate alone
```

---

## 8. Z-Test

### When to Use

- Population standard deviation **σ is KNOWN**
- Sample size n ≥ 30
- Data approximately normally distributed

### Formula

```
Z = (x̄ − μ₀) / (σ / √n)

x̄  = sample mean
μ₀ = hypothesized population mean (from H₀)
σ  = known population standard deviation
n  = sample size
```

### Numerical Example — College Placement

```
Claim: Placement rate = 85%
Sample: 200 students → 78% placed
σ = 5%, α = 0.05

H₀: μ = 85%
H₁: μ ≠ 85%  (two-tailed)

Z = (78 − 85) / (5/√200)
  = −7 / 0.354
  = −19.77

Critical Z (two-tailed, α=0.05) = ±1.96
|Z| = 19.77 > 1.96  →  REJECT H₀

Conclusion: Strong evidence placement rate is NOT 85%
```

---

## 9. t-Test

### When to Use

- Population standard deviation **σ is UNKNOWN** (use sample s)
- Especially when n < 30
- Data approximately normally distributed

### Formula

```
t = (x̄ − μ₀) / (s / √n)

x̄  = sample mean
μ₀ = hypothesized population mean
s  = sample standard deviation
n  = sample size
df = n − 1  (degrees of freedom)
```

### Degrees of Freedom (df = n−1)

```
Small df → fatter tails → more conservative test
Large df → t-distribution ≈ normal distribution
```

### Numerical Example — HR T-Shirt Sampling

```
Assume avg height = 170 cm
Sample: 15 employees → x̄ = 173 cm, s = 6 cm, α = 0.05

H₀: μ = 170
H₁: μ ≠ 170  (two-tailed)
df = 14

t = (173 − 170) / (6/√15)
  = 3 / 1.549
  = 1.937

Critical t (df=14, two-tailed, α=0.05) = ±2.145
|t| = 1.937 < 2.145  →  FAIL TO REJECT H₀

Conclusion: Not enough evidence average height ≠ 170 cm
            → Order standard sizing
```

### Z-Test vs t-Test

| Feature | Z-Test | t-Test |
|---------|--------|--------|
| σ known? | Yes ✅ | No — use s |
| Sample size | n ≥ 30 | Any n (especially n < 30) |
| Distribution | Normal (Z) | t-distribution |
| Degrees of freedom | N/A | df = n−1 |
| Tail shape | Thinner | Fatter (more conservative) |

---

## 10. One-Tailed vs Two-Tailed Test

### Two-Tailed Test

H₁ says parameter is **different** (either direction).

```
H₀: μ = 50
H₁: μ ≠ 50   ← two-tailed

α = 0.05 → split as α/2 = 0.025 on each side

Reject if Z < −1.96  OR  Z > +1.96

  Reject  |   Fail to Reject   | Reject
──────────┼────────────────────┼──────────
  −1.96   |                    | +1.96
```

### One-Tailed Test

H₁ says parameter is **specifically higher or lower**.

```
Right-tailed:     H₁: μ > 50  →  Reject if Z > +1.645
Left-tailed:      H₁: μ < 50  →  Reject if Z < −1.645
```

### Critical Values Summary

| Test Type | α = 0.05 | α = 0.01 |
|-----------|----------|----------|
| Two-tailed | ±1.960 | ±2.576 |
| Right-tailed | +1.645 | +2.326 |
| Left-tailed | −1.645 | −2.326 |

### When to Use Which

| Question | Test |
|----------|------|
| "Is it different?" | Two-tailed |
| "Is it higher?" | Right one-tailed |
| "Is it lower?" | Left one-tailed |
| Not sure of direction | Two-tailed (safer default) |

---

## 11. Practical Examples

### Example 1 — CAT Exam Confidence Interval

```
Data: n=64, x̄=120, σ=16, 95% CI

SE = 16/√64 = 2
ME = 1.96 × 2 = 3.92

CI = [116.08, 123.92]
→ 95% confident true avg CAT score is between 116 and 124
```

### Example 2 — College Placement Rate

```
Claim: 90% placement. Survey: n=100, 84% placed. σ=8%, α=0.05

H₀: μ = 90%
H₁: μ < 90%   (left-tailed — we think it's LOWER)

Z = (84−90) / (8/√100) = −6/0.8 = −7.5
Critical Z (left, α=0.05) = −1.645
−7.5 < −1.645  →  REJECT H₀
Conclusion: Evidence placement rate is below 90%
```

### Example 3 — Manager Business Decision

```
Manager says avg order = ₹500. Team samples 36 orders.
x̄=₹480, s=₹60 (σ unknown → t-test), α=0.05

H₀: μ = ₹500
H₁: μ ≠ ₹500   (two-tailed)
df = 35

t = (480−500) / (60/√36) = −20/10 = −2.0
Critical t (df=35, two-tailed) ≈ ±2.030

|t| = 2.0 < 2.030  →  FAIL TO REJECT H₀
Conclusion: Borderline — not enough evidence avg order ≠ ₹500
```

### Example 4 — HR T-Shirt Sizing

```
Assume avg height = 170cm. Sample 15 employees.
x̄=174, s=5, α=0.05

H₀: μ = 170
H₁: μ > 170   (right-tailed — ordering larger sizes)
df = 14

t = (174−170) / (5/√15) = 4/1.29 = 3.1
Critical t (df=14, right-tailed) = 1.761

3.1 > 1.761  →  REJECT H₀
Conclusion: Employees are taller → Order larger T-shirt sizes
```

---

## 12. Interview Q&A

| Question | Model Answer |
|----------|-------------|
| **Pearson vs Spearman?** | Pearson: linear, continuous, normal data. Spearman: rank-based, ordinal/skewed/outliers. Use Spearman when Pearson's assumptions are violated. |
| **How to use correlation for feature selection?** | Build correlation matrix. |r| > 0.85 between features = multicollinearity → drop one. Near-zero with target = weak predictor → drop it. |
| **What is a p-value?** | Probability of seeing your result (or more extreme) if H₀ is true. Small p → unlikely under H₀ → reject it. |
| **Why never "accept H₀"?** | Failing to reject means insufficient evidence to disprove it — not that it's true. Absence of evidence ≠ evidence of absence. |
| **Z-test vs t-test?** | Z-test: σ known, n≥30. t-test: σ unknown (use s), especially n<30. t has fatter tails for added uncertainty. |
| **What does 95% CI mean?** | If we sampled 100 times and built 100 CIs, ~95 would contain the true μ. NOT a 95% probability for this specific interval. |
| **α and confidence level relationship?** | Confidence Level = 1 − α. At α=0.05, we have 95% confidence. We accept 5% risk of Type I error (wrongly rejecting true H₀). |
| **One-tailed vs two-tailed?** | Two-tailed: testing if different in either direction (≠). One-tailed: specifically higher (>) or lower (<). Two-tailed is more conservative. |
| **What is Standard Error?** | SE = σ/√n. Measures precision of sample mean as estimate of μ. Larger n → smaller SE → more precise. |

---

## 13. Quick Reference Cheat Sheet

```
CORRELATION
──────────────────────────────────────────────────
Pearson  r  = Cov(X,Y) / (σₓ × σᵧ)   → linear, normal
Spearman rₛ = 1 − 6Σd²/n(n²−1)        → rank-based, robust
Range: −1 ≤ r ≤ +1
|r| > 0.85 between features → multicollinearity → drop one
~0 with target → weak predictor → drop it

HYPOTHESIS TESTING
──────────────────────────────────────────────────
1. State H₀ and H₁
2. Set α (0.05 standard)
3. Choose test (Z or t)
4. Calculate test statistic
5. p < α → Reject H₀ | p ≥ α → Fail to Reject
NEVER say "Accept H₀"

CONFIDENCE INTERVAL
──────────────────────────────────────────────────
CI = x̄ ± Z* × (σ/√n)
90% → Z* = 1.645
95% → Z* = 1.960
99% → Z* = 2.576
CI narrows with ↑n | widens with ↑σ or ↑confidence

Z-TEST vs T-TEST
──────────────────────────────────────────────────
Z = (x̄ − μ₀) / (σ/√n)    → σ known, n≥30
t = (x̄ − μ₀) / (s/√n)    → σ unknown, df = n−1

CRITICAL VALUES (α = 0.05)
──────────────────────────────────────────────────
Two-tailed   → ±1.960
Right-tailed → +1.645
Left-tailed  → −1.645

P-VALUE
──────────────────────────────────────────────────
p < α  → Reject H₀
p ≥ α  → Fail to Reject H₀
```

---

## 🔗 Connect

- 🐙 GitHub: [@mmtiwari222](https://github.com/mmtiwari222)
- 💼 LinkedIn: Learning in public | Aspiring Data Analyst
- 📓 Full notes with examples → Notion

---

*Day 5 of Statistics for Data Analysis. Part of my DA → DS → ML → AI learning journey. 🚀*
