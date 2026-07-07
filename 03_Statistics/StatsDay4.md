# 📊 Statistics Day 4 — Z-Score, CLT, Probability, Permutation, Combination & Covariance

> **Learning Track:** DA → DS → ML → AI | **Date:** July 6, 2026
> **Author:** [@mmtiwari222](https://github.com/mmtiwari222) | Learning in public. Building in public. 🚀

---

## 📌 Topics Covered

| #   | Topic                                                                                       |
| --- | ------------------------------------------------------------------------------------------- |
| 1   | [Z-Score — Formula, Z-Table, Area Under Curve](#1-z-score-formula-z-table-area-under-curve) |
| 2   | [Central Limit Theorem (CLT)](#2-central-limit-theorem-clt)                                 |
| 3   | [Probability — All Rules](#3-probability-all-rules)                                         |
| 4   | [Permutation](#4-permutation)                                                               |
| 5   | [Combination](#5-combination)                                                               |
| 6   | [Covariance](#6-covariance)                                                                 |
| 7   | [Pearson & Spearman Correlation — Intro](#7-pearson--spearman-correlation--intro)           |
| 8   | [Interview Q&A](#8-interview-qa)                                                            |
| 9   | [Quick Reference Cheat Sheet](#9-quick-reference-cheat-sheet)                               |

---

## 1. Z-Score: Formula, Z-Table, Area Under Curve

### Z-Score Formula

```
Population:  Z = (x − μ) / σ
Sample Mean: Z = (x̄ − μ) / (σ / √n)

x = individual data point
μ = mean
σ = standard deviation
n = sample size
```

### Z-Table

The Z-table gives **cumulative probability** (area under curve) to the **LEFT** of a Z-score.

| Z-Score | Area to LEFT | Area to RIGHT |
| ------- | ------------ | ------------- |
| −3.00   | 0.0013       | 0.9987        |
| −2.00   | 0.0228       | 0.9772        |
| −1.00   | 0.1587       | 0.8413        |
| 0.00    | 0.5000       | 0.5000        |
| +1.00   | 0.8413       | 0.1587        |
| +2.00   | 0.9772       | 0.0228        |
| +3.00   | 0.9987       | 0.0013        |

### Area Under the Normal Curve

Total area under curve = **1 (100% probability)**

```
Area to LEFT   of Z     = P(X < a) = Z-table value
Area to RIGHT  of Z     = P(X > a) = 1 − Z-table value
Area BETWEEN   Z1 & Z2  = P(a < X < b) = CDF(Z2) − CDF(Z1)
```

### 3 Types of Probability Problems

**Type 1 — P(X < a) → Area to LEFT**

```
Scores: μ=70, σ=10. What is P(score < 85)?
Z = (85 − 70) / 10 = 1.5
P(X < 85) = 0.9332 = 93.32%
```

**Type 2 — P(X > a) → Area to RIGHT**

```
P(score > 85) = 1 − 0.9332 = 0.0668 = 6.68%
```

**Type 3 — P(a < X < b) → Area BETWEEN**

```
P(60 < score < 85) = ?
Z1 = (60−70)/10 = −1.0 → 0.1587
Z2 = (85−70)/10 = +1.5 → 0.9332
P = 0.9332 − 0.1587 = 0.7745 = 77.45%
```

> 💡 **Interview Tip:** Always draw the curve and shade the region first. Prevents wrong subtraction mistakes.

---

## 2. Central Limit Theorem (CLT)

### What is CLT?

> Regardless of population distribution shape, the distribution of **sample means** approaches **normal distribution** as sample size increases — provided **n ≥ 30**.

### Key Terms

| Term            | Symbol    | Description                       |
| --------------- | --------- | --------------------------------- |
| Population Mean | μ         | True average of entire population |
| Population SD   | σ         | True spread of entire population  |
| Sample Mean     | x̄         | Average of one sample             |
| Standard Error  | SE = σ/√n | SD of the sampling distribution   |

### How CLT Works

```
Population (ANY shape — skewed, uniform, bimodal)
     ↓
Take many samples of size n ≥ 30
     ↓
Calculate mean of each sample (x̄₁, x̄₂, x̄₃...)
     ↓
Plot all those sample means
     ↓
Result = Normal Distribution!
         Center = μ
         Spread = σ/√n  (Standard Error)
```

### n ≥ 30 Rule

| Sample Size               | Behaviour                                    |
| ------------------------- | -------------------------------------------- |
| n < 30                    | May not be normal → use t-distribution       |
| n ≥ 30                    | CLT applies → sampling distribution ≈ normal |
| Population already normal | CLT applies for ANY n                        |

### Standard Error

```
SE = σ / √n

↑ n increases  →  SE decreases  →  sample means cluster closer to μ
↑ Larger sample = more reliable, more precise estimate
```

### Real Industry Example

```
Scenario: Customer satisfaction scores (1–10), skewed distribution
          Most customers rate 8–10, very few rate 1–3

Action:   Take 50 random samples of 40 customers each
          Calculate mean score for each sample
          Plot those 50 means

Result:   Even though raw scores are right-skewed,
          the 50 sample means form a bell curve
          → CLT in action
          → Now we can run hypothesis tests, build confidence intervals
```

> 💡 **Interview Answer:** _"CLT is what makes statistical inference possible in the real world — where data is rarely normal. Sample means become normal for large enough n, so we can use normal-based tests even on non-normal populations."_

---

## 3. Probability: All Rules

### Basic Probability

```
P(Event) = Favorable outcomes / Total outcomes

0 ≤ P(A) ≤ 1
P(impossible) = 0
P(certain)    = 1
P(A) + P(A')  = 1   ← Complement rule
```

**Classic Examples:**

```
Coin:   P(Heads)      = 1/2 = 0.5
Dice:   P(getting 4)  = 1/6 ≈ 0.167
Marble: 3 red, 2 blue → P(red) = 3/5 = 0.6
```

---

### Bernoulli Distribution

Exactly **two outcomes**: Success (1) or Failure (0).

```
P(Success) = p
P(Failure) = 1 − p = q

Mean     = p
Variance = p(1−p) = pq
```

| Scenario      | Success (p)      | Failure (1−p)     |
| ------------- | ---------------- | ----------------- |
| Coin toss     | Heads (0.5)      | Tails (0.5)       |
| Email click   | Clicked (0.3)    | Not clicked (0.7) |
| Quality check | Defective (0.02) | Pass (0.98)       |

> 💡 Bernoulli = building block of Binomial Distribution (n repeated Bernoulli trials)

---

### Mutually Exclusive Events

Events that **cannot happen at the same time** — no overlap.

```
P(A ∩ B) = 0
P(A ∪ B) = P(A) + P(B)   ← Addition Rule for ME events
```

**Examples:**

- Dice: getting 3 AND getting 5 in one roll ✅ Mutually exclusive
- Coin: Heads AND Tails simultaneously ✅ Mutually exclusive

---

### Non-Mutually Exclusive Events

Events that **can happen at the same time** — overlap exists.

```
P(A ∪ B) = P(A) + P(B) − P(A ∩ B)   ← Addition Rule (General)
```

**Example:**

```
From a deck of 52 cards:
P(King)          = 4/52
P(Heart)         = 13/52
P(King of Hearts) = 1/52   ← overlap

P(King OR Heart) = 4/52 + 13/52 − 1/52 = 16/52 ≈ 0.308
```

---

### Addition Rule Summary

```
Mutually Exclusive:      P(A∪B) = P(A) + P(B)
Non-Mutually Exclusive:  P(A∪B) = P(A) + P(B) − P(A∩B)
```

---

### Independent Events

Occurrence of one does **NOT affect** the other.

```
P(A ∩ B) = P(A) × P(B)   ← Multiplication Rule for Independent
```

**Examples:**

- Tossing a coin twice
- Rolling two dice simultaneously

**Worked Example:**

```
P(Heads toss 1) = 0.5
P(Heads toss 2) = 0.5
P(Both Heads)   = 0.5 × 0.5 = 0.25
```

---

### Dependent Events

Occurrence of one **DOES affect** the other.

**Examples:**

- Drawing marbles WITHOUT replacement
- Drawing cards WITHOUT replacement

**Worked Example:**

```
Bag: 3 Red, 2 Blue marbles (5 total)

P(Red first)              = 3/5
P(Red second | Red first) = 2/4   ← bag now has 4 marbles

P(Both Red) = 3/5 × 2/4 = 6/20 = 0.30
```

---

### Multiplication Rule Summary

```
Independent: P(A ∩ B) = P(A) × P(B)
Dependent:   P(A ∩ B) = P(A) × P(B|A)
```

---

### Conditional Probability

Probability of B occurring **given that** A has already occurred.

```
P(B|A) = P(A ∩ B) / P(A)
```

**Biscuit Example:**

```
Box: 6 Chocolate + 4 Vanilla = 10 biscuits
One Chocolate already eaten (9 remain, 5 Chocolate)

P(Chocolate | first was Chocolate) = 5/9
```

**Real Industry Example:**

```
In a company:
P(Employee in Sales)          = 0.40
P(Employee hit target)        = 0.30
P(Sales AND hit target)       = 0.20

P(hit target | in Sales) = 0.20 / 0.40 = 0.50
→ 50% of Sales employees hit their target
```

> 💡 **Interview Tip:** _"Conditional probability is the foundation of Bayes' Theorem — which powers Naive Bayes classifiers, spam filters, and medical diagnosis models."_

---

### Classic Examples Summary

| Scenario                    | Type               | Calculation         |
| --------------------------- | ------------------ | ------------------- | --- |
| Coin — P(Heads)             | Basic              | 1/2                 |
| Dice — P(even)              | Basic              | 3/6 = 0.5           |
| Dice — P(2 OR 5)            | Mutually Exclusive | 1/6 + 1/6 = 2/6     |
| Cards — P(King OR Heart)    | Non-ME             | 4/52 + 13/52 − 1/52 |
| 2 Coins — P(HH)             | Independent        | 1/2 × 1/2 = 1/4     |
| Marbles without replacement | Dependent          | `P(A) × P(B         | A)` |
| Biscuit 2nd given 1st       | Conditional        | `P(A∩B) / P(A)`     |

---

## 4. Permutation

### What is Permutation?

Number of ways to **arrange** items where **ORDER MATTERS**.

```
ⁿPᵣ = n! / (n − r)!

n = total items
r = items being arranged
! = factorial  →  5! = 5×4×3×2×1 = 120
```

### When to Use

- Ranking top performers
- Creating passwords / PIN codes
- Seating arrangements
- Race finishing positions

### Worked Examples

```
Example 1: Arrange 3 students from a group of 5
n=5, r=3
⁵P₃ = 5! / (5−3)! = 120 / 2 = 60 ways

Example 2: 3-digit PIN from digits 1–9 (no repetition)
n=9, r=3
⁹P₃ = 9! / (9−3)! = 9×8×7 = 504 PINs
```

**Real Industry Example:**

```
HR ranking: 8 candidates for 1st, 2nd, 3rd position
⁸P₃ = 8×7×6 = 336 possible rankings
```

> 💡 **Memory Rule:** "Arrange", "rank", "sequence", "order" = **P**ermutation → **P**osition matters

---

## 5. Combination

### What is Combination?

Number of ways to **select** items where **ORDER DOES NOT MATTER**.

```
ⁿCᵣ = n! / (r! × (n − r)!)

n = total items
r = items being selected
```

### When to Use

- Selecting a team from a group
- Choosing lottery numbers
- Picking items from a menu
- Selecting features for a model

### Worked Examples

```
Example 1: Select 3 students from a group of 5
n=5, r=3
⁵C₃ = 5! / (3! × 2!) = 120 / 12 = 10 ways

Example 2: Lottery — choose 6 from 49
⁴⁹C₆ = 13,983,816 combinations
P(winning) = 1 / 13,983,816
```

**Real Industry Example:**

```
Data Science: Choose 4 features from 10 for a model
¹⁰C₄ = 10! / (4! × 6!) = 210 possible feature sets
```

---

### Permutation vs Combination

|                  | Permutation                    | Combination                 |
| ---------------- | ------------------------------ | --------------------------- |
| **Order**        | Matters ✅                     | Does NOT matter ❌          |
| **Formula**      | n! / (n−r)!                    | n! / (r!(n−r)!)             |
| **Result count** | More (arrangements)            | Less (selections)           |
| **Keywords**     | arrange, rank, order, sequence | choose, select, pick, group |
| **Example**      | Top 3 race finish              | Team of 3 from group        |

> 💡 **Memory Trick:** **P**ermutation = **P**osition matters. **C**ombination = just a **C**ollection.

---

## 6. Covariance

### What is Covariance?

Measures the **direction of relationship** between two variables — do they move together or in opposite directions?

```
Population Covariance:
Cov(X,Y) = Σ[(xᵢ − μₓ)(yᵢ − μᵧ)] / N

Sample Covariance:
Cov(X,Y) = Σ[(xᵢ − x̄)(yᵢ − ȳ)] / (n−1)
```

### Positive vs Negative Covariance

| Value       | Meaning                        | Example                  |
| ----------- | ------------------------------ | ------------------------ |
| **Cov > 0** | Both increase together         | Study hours & exam score |
| **Cov < 0** | One increases, other decreases | Price & demand           |
| **Cov = 0** | No linear relationship         | Shoe size & salary       |

```
Positive: X↑ → Y↑  (same direction)
Negative: X↑ → Y↓  (opposite direction)
```

### Cov(X, X) = Variance

```
Cov(X, X) = Σ[(xᵢ − x̄)(xᵢ − x̄)] / (n−1)
           = Σ[(xᵢ − x̄)²] / (n−1)
           = Variance of X
```

> Variance is a special case of covariance — when both variables are the same!

### Numerical Example

```
Hours Studied (X): 2,  4,  6,  8
Exam Score    (Y): 50, 60, 75, 85

x̄ = (2+4+6+8)/4 = 5
ȳ = (50+60+75+85)/4 = 67.5

x    xᵢ−x̄    y    yᵢ−ȳ    (xᵢ−x̄)(yᵢ−ȳ)
2    −3      50   −17.5      52.5
4    −1      60    −7.5       7.5
6    +1      75    +7.5       7.5
8    +3      85   +17.5      52.5
                         ──────────
              Sum =        120

Sample Cov(X,Y) = 120 / (4−1) = 40

Cov = +40 → Positive → More study = Higher score ✅
```

### Real Industry Examples

| X Variable         | Y Variable      | Expected Cov |
| ------------------ | --------------- | ------------ |
| Ad spend           | Revenue         | Positive     |
| Product price      | Units sold      | Negative     |
| Experience (years) | Salary          | Positive     |
| Temperature        | Hot drink sales | Negative     |
| Page load time     | Conversion rate | Negative     |

### Limitation of Covariance

```
Cov = 40    vs    Cov = 4000
Both positive — but which relationship is STRONGER?
Cannot tell from covariance alone!
Value depends on units → not comparable across datasets
```

> This is why we need **Correlation** — normalizes covariance to −1 to +1 scale.

---

## 7. Pearson & Spearman Correlation — Intro

### What is Correlation?

Measures both **direction AND strength** of relationship between two variables.

```
Range: −1 ≤ r ≤ +1

r = +1  →  Perfect positive linear relationship
r =  0  →  No linear relationship
r = −1  →  Perfect negative linear relationship
```

### Pearson Correlation

```
r = Cov(X,Y) / (σₓ × σᵧ)

= Covariance normalized by product of standard deviations
```

| r value   | Interpretation                     |
| --------- | ---------------------------------- |
| 0.9 – 1.0 | Very strong positive               |
| 0.7 – 0.9 | Strong positive                    |
| 0.5 – 0.7 | Moderate positive                  |
| 0.3 – 0.5 | Weak positive                      |
| 0.0 – 0.3 | Very weak / negligible             |
| Negative  | Same magnitude, opposite direction |

**Use when:** Continuous, normally distributed data, linear relationship

---

### Spearman Rank Correlation

- Uses **ranks** instead of raw values
- Measures **monotonic** relationship (not necessarily linear)
- More **robust to outliers** than Pearson
- Works with **ordinal data**

```
Convert values to ranks → Apply correlation on those ranks
```

**Use when:** Ordinal data, skewed distributions, outliers present

---

### Pearson vs Spearman

| Situation                  | Use      |
| -------------------------- | -------- |
| Continuous, normal, linear | Pearson  |
| Ordinal data               | Spearman |
| Outliers present           | Spearman |
| Skewed data                | Spearman |
| Non-linear but monotonic   | Spearman |

**Real Industry Examples:**

| X                           | Y               | Use      |
| --------------------------- | --------------- | -------- |
| Ad spend (₹)                | Revenue (₹)     | Pearson  |
| Customer satisfaction rank  | Repurchase rank | Spearman |
| Employee performance rating | Bonus tier      | Spearman |
| Temperature                 | Ice cream sales | Pearson  |

> 💡 **Interview Tip:** _"Pearson for normally distributed continuous data. Spearman for ordinal, skewed, or data with outliers. Spearman is rank-based — more robust but captures less information than Pearson on clean data."_

---

## 8. Interview Q&A

| Question                                | Model Answer                                                                                                                             |
| --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **Left vs Right area in Z-table?**      | Z-table gives left (cumulative) area by default. Right = 1 − left. Between two Z-scores = CDF(Z2) − CDF(Z1).                             |
| **What is CLT and why does it matter?** | Sample means are normally distributed for n≥30 regardless of population shape. Enables normal-based tests on non-normal real-world data. |
| **What is Standard Error?**             | SE = σ/√n. SD of the sampling distribution. Larger sample → smaller SE → more precise estimates.                                         |
| **Mutually exclusive vs independent?**  | ME = cannot happen together (P(A∩B)=0). Independent = one doesn't affect other (P(A∩B)=P(A)×P(B)). ME events are actually DEPENDENT.     |
| **Permutation vs Combination?**         | Permutation when order matters (rankings, PINs). Combination when order doesn't matter (teams, selections).                              |
| **What does Cov(X,X) equal?**           | Variance of X. Covariance of a variable with itself = average squared deviation = variance.                                              |
| **Limitation of covariance?**           | Tells direction but not strength. Value depends on units, making cross-dataset comparison impossible. Correlation solves this.           |
| **Pearson vs Spearman?**                | Pearson for continuous normal linear data. Spearman for ordinal/skewed/outlier data — it's rank-based and more robust.                   |
| **What is conditional probability?**    | P(B\|A) = P(A∩B)/P(A). Probability of B given A already occurred. Foundation of Bayes' Theorem.                                          |

---

## 9. Quick Reference Cheat Sheet

```
Z-SCORE & AREA
───────────────────────────────────────────────
Z = (x − μ) / σ
Left area  = P(X < a) = CDF(Z)
Right area = P(X > a) = 1 − CDF(Z)
Between    = CDF(Z2) − CDF(Z1)

CENTRAL LIMIT THEOREM
───────────────────────────────────────────────
Sample mean distribution: x̄ ~ N(μ, σ²/n)
Standard Error: SE = σ / √n
n ≥ 30 → sampling distribution ≈ Normal

PROBABILITY RULES
───────────────────────────────────────────────
Basic:             P(A) = favorable / total
Complement:        P(A') = 1 − P(A)
Addition (ME):     P(A∪B) = P(A) + P(B)
Addition (general):P(A∪B) = P(A) + P(B) − P(A∩B)
Multiplication (I):P(A∩B) = P(A) × P(B)
Multiplication (D):P(A∩B) = P(A) × P(B|A)
Conditional:       P(B|A) = P(A∩B) / P(A)

BERNOULLI
───────────────────────────────────────────────
P(Success) = p  |  P(Failure) = 1−p
Mean = p  |  Variance = p(1−p)

PERMUTATION & COMBINATION
───────────────────────────────────────────────
ⁿPᵣ = n! / (n−r)!          → Order MATTERS
ⁿCᵣ = n! / (r! × (n−r)!)   → Order does NOT matter

COVARIANCE
───────────────────────────────────────────────
Cov(X,Y) = Σ[(xᵢ−x̄)(yᵢ−ȳ)] / (n−1)
Cov > 0 → same direction
Cov < 0 → opposite direction
Cov(X,X) = Variance(X)

CORRELATION
───────────────────────────────────────────────
Pearson r = Cov(X,Y) / (σₓ × σᵧ)   → linear, normal data
Spearman  → rank-based, ordinal/skewed data
Range: −1 ≤ r ≤ +1
```

---

## 🔗 Connect

- 🐙 GitHub: [@mmtiwari222](https://github.com/mmtiwari222)
- 💼 LinkedIn: Learning in public | Aspiring Data Analyst
- 📓 Full notes with examples → Notion

---

_Day 4 of Statistics for Data Analysis. Part of my DA → DS → ML → AI learning journey. 🚀_
