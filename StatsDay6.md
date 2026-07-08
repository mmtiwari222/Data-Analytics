# 📊 Statistics Day 6 — Z-Test, T-Test Deep Dive, One-Tailed Tests, Proportion Test & Advanced Problems

> **Learning Track:** DA → DS → ML → AI | **Date:** July 8, 2026
> **Author:** [@mmtiwari222](https://github.com/mmtiwari222) | Learning in public. Building in public. 🚀

---

## 📌 Topics Covered

| # | Topic |
|---|-------|
| 1 | [Z-Test Conditions](#1-z-test--conditions) |
| 2 | [T-Test Conditions](#2-t-test--conditions) |
| 3 | [Z-Test vs T-Test](#3-z-test-vs-t-test--complete-comparison) |
| 4 | [One-Tailed Z-Test](#4-one-tailed-z-test) |
| 5 | [One-Tailed T-Test](#5-one-tailed-t-test) |
| 6 | [Z-Test for Population Proportion](#6-z-test-for-population-proportion) |
| 7 | [P-Value from Z-Score](#7-p-value-calculation-from-z-score) |
| 8 | [Advanced Numerical Problems](#8-advanced-numerical-problems) |
| 9 | [Interview Q&A](#9-interview-qa) |
| 10 | [Quick Reference](#10-quick-reference-cheat-sheet) |

---

## 1. Z-Test — Conditions

```
Condition 1: Population Standard Deviation (σ) is KNOWN
Condition 2: Sample size n ≥ 30 (CLT ensures normality)

Rules:
→ σ known           → Z-test (any n)
→ n ≥ 30            → Z-test (even if σ unknown, use s as approximation)
→ σ known + n ≥ 30  → Z-test (ideal scenario)
```

### Formula

```
For Mean:
Z = (x̄ − μ₀) / (σ / √n)

For Proportion:
Z = (p̂ − p₀) / √[p₀(1−p₀)/n]
```

---

## 2. T-Test — Conditions

```
Condition 1: Population SD (σ) is UNKNOWN → use sample s
Condition 2: Sample size n < 30 (small sample)

Rules:
→ σ unknown + n < 30  → t-test (must)
→ σ unknown + n ≥ 30  → t-test preferred (Z also acceptable via CLT)
```

### Formula

```
t = (x̄ − μ₀) / (s / √n)

s  = sample standard deviation
df = n − 1

As df increases → t-distribution → approaches normal
At df ≥ 120    → t ≈ Z
```

---

## 3. Z-Test vs T-Test — Complete Comparison

| Feature | Z-Test | T-Test |
|---------|--------|--------|
| **σ known?** | Yes ✅ | No — use s |
| **Sample size** | n ≥ 30 | n < 30 (or any when σ unknown) |
| **Distribution** | Standard Normal | t-distribution |
| **Degrees of freedom** | Not needed | df = n−1 |
| **Tail shape** | Thinner | Fatter (more conservative) |
| **Formula** | Z = (x̄−μ₀)/(σ/√n) | t = (x̄−μ₀)/(s/√n) |
| **Table used** | Z-table | t-table (with df) |

### Decision Flowchart

```
Is population σ known?
        │
   ┌────┴────┐
  YES        NO
   │          │
Z-Test    Is n ≥ 30?
           │        │
          YES       NO
           │         │
      Z or T-Test  T-Test
      (both valid)  (must)
```

> 💡 **Key Insight:** The only real difference is certainty about σ. When σ is known → Z. When estimated with s → t. Fatter t-tails account for the extra uncertainty of estimating σ.

---

## 4. One-Tailed Z-Test

### Left-Tailed Z-Test

```
H₀: μ = μ₀
H₁: μ < μ₀   ← LEFT-tailed

Reject H₀ if: Z < −Zα

α = 0.05 → Reject if Z < −1.645
α = 0.01 → Reject if Z < −2.326

All rejection area is on the LEFT side
```

**Example:**
```
Claim: Machine produces bolts avg length ≥ 50mm
Suspicion: Bolts are shorter (under-producing)

H₀: μ = 50mm
H₁: μ < 50mm   ← left-tailed
```

---

### Right-Tailed Z-Test

```
H₀: μ = μ₀
H₁: μ > μ₀   ← RIGHT-tailed

Reject H₀ if: Z > +Zα

α = 0.05 → Reject if Z > +1.645
α = 0.01 → Reject if Z > +2.326

All rejection area is on the RIGHT side
```

**Example:**
```
Claim: Training program improves avg score above 75

H₀: μ = 75
H₁: μ > 75   ← right-tailed
```

---

### Critical Values — All Scenarios

| Test Type | α = 0.10 | α = 0.05 | α = 0.01 |
|-----------|----------|----------|----------|
| Two-tailed | ±1.645 | ±1.960 | ±2.576 |
| Right-tailed | +1.282 | +1.645 | +2.326 |
| Left-tailed | −1.282 | −1.645 | −2.326 |

---

## 5. One-Tailed T-Test

Same logic as Z-test one-tailed, but uses t-distribution with df = n−1.

```
Left-tailed:  H₁: μ < μ₀ → Reject if t < −t(α, df)
Right-tailed: H₁: μ > μ₀ → Reject if t > +t(α, df)
```

**Example — School Students Weight (Right-tailed):**

```
Nutritionist claims students weigh > 40 kg on average
Sample: n=12, x̄=43kg, s=5kg, α=0.05

H₀: μ = 40
H₁: μ > 40   (right-tailed)
df = 11

t = (43 − 40) / (5/√12)
  = 3 / 1.443
  = 2.079

Critical t (df=11, right-tailed, α=0.05) = 1.796
2.079 > 1.796  →  REJECT H₀

Conclusion: Evidence supports avg weight > 40kg
```

---

## 6. Z-Test for Population Proportion

### When to Use

When the variable is **categorical / binary** (yes/no, pass/fail, own/don't own).

```
Conditions:
np₀ ≥ 5   AND   n(1−p₀) ≥ 5   (sufficient counts in both categories)
Random sample + independent observations
```

### Formula

```
Z = (p̂ − p₀) / √[p₀(1−p₀) / n]

p̂  = sample proportion = x / n   (x = number of successes)
p₀  = hypothesized population proportion
n   = sample size
```

### Step-by-Step

```
Step 1: State H₀ and H₁
Step 2: Calculate p̂ = x / n
Step 3: SE = √[p₀(1−p₀) / n]
Step 4: Z = (p̂ − p₀) / SE
Step 5: Find critical Z or p-value
Step 6: Decision
```

### Example 1 — Cell Phone Ownership

```
Claim: 70% of adults own a smartphone
Survey: n=200, 126 own smartphones, α=0.05

H₀: p = 0.70
H₁: p ≠ 0.70   (two-tailed)

p̂ = 126/200 = 0.63

SE = √[0.70 × 0.30 / 200]
   = √[0.21/200]
   = √0.00105
   = 0.0324

Z = (0.63 − 0.70) / 0.0324
  = −0.07 / 0.0324
  = −2.16

Critical Z (two-tailed, α=0.05) = ±1.96
|Z| = 2.16 > 1.96  →  REJECT H₀

p-value = 2 × (1 − Φ(2.16)) = 2 × (1 − 0.9846) = 0.0308
0.0308 < 0.05  →  REJECT H₀ ✓

Conclusion: Evidence that smartphone ownership ≠ 70%
```

### Example 2 — Vehicle Ownership

```
Claim: 45% households own a vehicle
Survey: n=300, 120 own vehicles, α=0.05

H₀: p = 0.45
H₁: p < 0.45   (left-tailed — suspect lower)

p̂ = 120/300 = 0.40

SE = √[0.45 × 0.55 / 300]
   = √0.000825
   = 0.02872

Z = (0.40 − 0.45) / 0.02872
  = −0.05 / 0.02872
  = −1.74

Critical Z (left-tailed, α=0.05) = −1.645
−1.74 < −1.645  →  REJECT H₀

Conclusion: Vehicle ownership is significantly less than 45%
```

---

## 7. P-Value Calculation from Z-Score

### Formula by Test Type

```
Φ(Z) = area to LEFT of Z from Z-table

Two-tailed:   p-value = 2 × (1 − Φ(|Z|))
Right-tailed: p-value = 1 − Φ(Z)
Left-tailed:  p-value = Φ(Z)
```

### Worked Example

```
Z = −2.16 (from Cell Phone example), Two-tailed

Φ(|−2.16|) = Φ(2.16) = 0.9846  (from Z-table)

p-value = 2 × (1 − 0.9846)
        = 2 × 0.0154
        = 0.0308

0.0308 < 0.05 (α)  →  REJECT H₀ ✓
```

### P-Value Interpretation

| P-Value | Meaning | Decision (α=0.05) |
|---------|---------|-------------------|
| 0.001 | 0.1% chance under H₀ | Very strong → Reject |
| 0.03 | 3% chance under H₀ | Strong → Reject |
| 0.05 | 5% chance — borderline | Check α exactly |
| 0.08 | 8% chance under H₀ | Fail to Reject |
| 0.25 | 25% chance under H₀ | Definitely Fail to Reject |

---

## 8. Advanced Numerical Problems

### Problem 1 — Machine Quality Testing

```
Claim: Machine produces bolts avg = 50mm, σ = 2mm
QC sample: n=40, x̄ = 49.2mm, α = 0.05
Is machine under-producing?

H₀: μ = 50mm
H₁: μ < 50mm   (left-tailed)
Test: Z-test (σ known, n=40 ≥ 30)

Z = (49.2 − 50) / (2/√40)
  = −0.8 / 0.316
  = −2.53

p-value = Φ(−2.53) = 0.0057
0.0057 < 0.05  →  REJECT H₀

✅ Conclusion: Machine IS under-producing. Maintenance required.
```

---

### Problem 2 — School Students' Weight

```
Health standard: avg student weight = 40kg
Sample: n=15, x̄=42.5kg, s=4.2kg, α=0.05
Are students heavier than standard?

H₀: μ = 40kg
H₁: μ > 40kg   (right-tailed)
Test: t-test (σ unknown, n=15 < 30)
df = 14

t = (42.5 − 40) / (4.2/√15)
  = 2.5 / 1.085
  = 2.304

Critical t (df=14, right-tailed, α=0.05) = 1.761
2.304 > 1.761  →  REJECT H₀

✅ Conclusion: Students are heavier than standard. Nutrition review needed.
```

---

### Problem 3 — Car Warranty Testing

```
Claim: Avg engine life = 5 years, σ = 0.8 years
Sample: n=50, x̄ = 4.7 years, α = 0.01
Is warranty claim valid?

H₀: μ = 5 years
H₁: μ < 5 years   (left-tailed)
Test: Z-test (σ known, n=50 ≥ 30)

Z = (4.7 − 5.0) / (0.8/√50)
  = −0.3 / 0.113
  = −2.655

Critical Z (left, α=0.01) = −2.326
p-value = Φ(−2.655) = 0.0040

−2.655 < −2.326 AND 0.004 < 0.01  →  REJECT H₀

✅ Conclusion: Engine life significantly below 5 years. Warranty claim NOT supported.
```

---

### Problem 4 — IQ Experiment

```
Claim: New study technique raises IQ above population avg of 100
Sample: n=20, x̄=104, s=12, α=0.05

H₀: μ = 100
H₁: μ > 100   (right-tailed)
Test: t-test (σ unknown, n=20 < 30)
df = 19

t = (104 − 100) / (12/√20)
  = 4 / 2.683
  = 1.491

Critical t (df=19, right-tailed, α=0.05) = 1.729
1.491 < 1.729  →  FAIL TO REJECT H₀

✅ Conclusion: Not enough evidence technique increases IQ. Larger sample needed.
```

---

### Problem 5 — Bike Battery Life

```
Claim: Avg battery life = 3.5 years, σ = 0.6 years
Sample: n=36, x̄ = 3.2 years, α = 0.05

H₀: μ = 3.5 years
H₁: μ < 3.5 years   (left-tailed)
Test: Z-test (σ known, n=36 ≥ 30)

Z = (3.2 − 3.5) / (0.6/√36)
  = −0.3 / 0.1
  = −3.0

p-value = Φ(−3.0) = 0.0013
0.0013 < 0.05  →  REJECT H₀

✅ Conclusion: Battery life significantly below 3.5 years. Strong evidence against claim.
```

---

### Problem 6 — Cell Phone Ownership Survey

```
Claim: 70% of adults own smartphones
Survey: n=200, 126 own, α=0.05

→ Solved in Section 6
Result: Z = −2.16, p = 0.0308 < 0.05  →  REJECT H₀
✅ Smartphone ownership ≠ 70%
```

---

### Problem 7 — Vehicle Ownership Survey

```
Claim: 45% households own a vehicle
Survey: n=300, 120 own, α=0.05

→ Solved in Section 6
Result: Z = −1.74, p ≈ 0.041 < 0.05  →  REJECT H₀
✅ Vehicle ownership < 45%
```

---

## 9. Interview Q&A

| Question | Model Answer |
|----------|-------------|
| **Exact conditions for Z vs t?** | Z-test: σ known OR n≥30. t-test: σ unknown, especially n<30. When n≥30 and σ unknown, both valid — t-test technically more correct. |
| **Why fatter tails in t-distribution?** | We estimate σ using s, which adds uncertainty. Fatter tails make the test more conservative — reduces false positives from that extra uncertainty. |
| **What changes in one-tailed vs two-tailed?** | Critical value and rejection region location. Two-tailed splits α across both sides. One-tailed puts all α on one side — more powerful in that direction but blind to effects in the opposite. |
| **When to use proportion Z-test?** | Binary variable (yes/no), np₀ ≥ 5 AND n(1−p₀) ≥ 5. Formula: Z = (p̂−p₀)/√[p₀(1−p₀)/n] |
| **How to get p-value from Z?** | Two-tailed: 2×(1−Φ(\|Z\|)). Right: 1−Φ(Z). Left: Φ(Z). Φ(Z) = left area from Z-table. |
| **Z-test with σ unknown and n≥30 — valid?** | Yes. CLT makes sampling distribution approximately normal, so Z-test is acceptable using s. But t-test is also valid and slightly more precise. |
| **What does p=0.0013 mean?** | 0.13% chance of seeing this result if H₀ is true. Very strong evidence against H₀ — reject with high confidence. |

---

## 10. Quick Reference Cheat Sheet

```
Z-TEST
──────────────────────────────────────────────────
Conditions: σ known  OR  n ≥ 30
Formula:    Z = (x̄ − μ₀) / (σ/√n)

T-TEST
──────────────────────────────────────────────────
Conditions: σ unknown  (especially n < 30)
Formula:    t = (x̄ − μ₀) / (s/√n),  df = n−1

PROPORTION Z-TEST
──────────────────────────────────────────────────
Z = (p̂ − p₀) / √[p₀(1−p₀)/n]
p̂ = x/n
Condition: np₀ ≥ 5  AND  n(1−p₀) ≥ 5

CRITICAL VALUES (α = 0.05)
──────────────────────────────────────────────────
Two-tailed   →  ±1.960
Right-tailed →  +1.645
Left-tailed  →  −1.645

CRITICAL VALUES (α = 0.01)
──────────────────────────────────────────────────
Two-tailed   →  ±2.576
Right-tailed →  +2.326
Left-tailed  →  −2.326

P-VALUE FROM Z-SCORE
──────────────────────────────────────────────────
Two-tailed:   p = 2 × (1 − Φ(|Z|))
Right-tailed: p = 1 − Φ(Z)
Left-tailed:  p = Φ(Z)
p < α  →  Reject H₀
p ≥ α  →  Fail to Reject H₀
```

---

## 🔗 Connect

- 🐙 GitHub: [@mmtiwari222](https://github.com/mmtiwari222)
- 💼 LinkedIn: Learning in public | Aspiring Data Analyst
- 📓 Full notes → Notion

---

*Day 6 of Statistics for Data Analysis. Part of my DA → DS → ML → AI learning journey. 🚀*
