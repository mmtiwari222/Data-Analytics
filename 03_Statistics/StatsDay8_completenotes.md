# 📊 Statistics for Data Analysis — Complete Notes (Day 1 to Day 7)

> **Learning Track:** DA → DS → ML → AI
> **Author:** [@mmtiwari222](https://github.com/mmtiwari222)
> **Coverage:** Every topic from Day 1 to Day 7 — small to large, nothing skipped.

---

## 📌 Table of Contents

| #  | Topic                                                                                         |
| -- | --------------------------------------------------------------------------------------------- |
| 1  | [What is Statistics](#1-what-is-statistics)                                                    |
| 2  | [Types of Statistics](#2-types-of-statistics)                                                  |
| 3  | [Descriptive Statistics](#3-descriptive-statistics)                                            |
| 4  | [Inferential Statistics](#4-inferential-statistics)                                            |
| 5  | [Population vs Sample](#5-population-vs-sample)                                                |
| 6  | [Sampling Techniques](#6-sampling-techniques)                                                  |
| 7  | [Variables &amp; Types](#7-variables--types)                                                   |
| 8  | [Qualitative Data](#8-qualitative-data)                                                        |
| 9  | [Quantitative Data](#9-quantitative-data)                                                      |
| 10 | [Distribution](#10-distribution)                                                               |
| 11 | [Range](#11-range)                                                                             |
| 12 | [Histogram](#12-histogram)                                                                     |
| 13 | [Mean](#13-mean)                                                                               |
| 14 | [Median](#14-median)                                                                           |
| 15 | [Mode](#15-mode)                                                                               |
| 16 | [Outlier](#16-outlier)                                                                         |
| 17 | [Dispersion](#17-dispersion)                                                                   |
| 18 | [Variance](#18-variance)                                                                       |
| 19 | [Bessel&#39;s Correction &amp; Degrees of Freedom](#19-bessels-correction--degrees-of-freedom) |
| 20 | [Standard Deviation](#20-standard-deviation)                                                   |
| 21 | [Percentile](#21-percentile)                                                                   |
| 22 | [Quartiles &amp; IQR](#22-quartiles--iqr)                                                      |
| 23 | [Five-Number Summary](#23-five-number-summary)                                                 |
| 24 | [Box Plot](#24-box-plot)                                                                       |
| 25 | [Normal Distribution (Gaussian)](#25-normal-distribution-gaussian)                             |
| 26 | [Empirical Rule (68-95-99.7)](#26-empirical-rule-68-95-997)                                    |
| 27 | [Standard Normal Distribution](#27-standard-normal-distribution)                               |
| 28 | [Z-Score](#28-z-score)                                                                         |
| 29 | [Z-Table &amp; Area Under Curve](#29-z-table--area-under-curve)                                |
| 30 | [Central Limit Theorem (CLT)](#30-central-limit-theorem-clt)                                   |
| 31 | [Standard Error](#31-standard-error)                                                           |
| 32 | [Basic Probability](#32-basic-probability)                                                     |
| 33 | [Bernoulli Distribution](#33-bernoulli-distribution)                                           |
| 34 | [Binomial Distribution](#34-binomial-distribution)                                             |
| 35 | [Mutually Exclusive Events](#35-mutually-exclusive-events)                                     |
| 36 | [Non-Mutually Exclusive Events](#36-non-mutually-exclusive-events)                             |
| 37 | [Addition Rule](#37-addition-rule)                                                             |
| 38 | [Independent Events](#38-independent-events)                                                   |
| 39 | [Dependent Events](#39-dependent-events)                                                       |
| 40 | [Multiplication Rule](#40-multiplication-rule)                                                 |
| 41 | [Conditional Probability](#41-conditional-probability)                                         |
| 42 | [Permutation](#42-permutation)                                                                 |
| 43 | [Combination](#43-combination)                                                                 |
| 44 | [Covariance](#44-covariance)                                                                   |
| 45 | [Pearson Correlation](#45-pearson-correlation)                                                 |
| 46 | [Spearman Rank Correlation](#46-spearman-rank-correlation)                                     |
| 47 | [Pearson vs Spearman](#47-pearson-vs-spearman)                                                 |
| 48 | [Feature Selection Using Correlation](#48-feature-selection-using-correlation)                 |
| 49 | [P-Value](#49-p-value)                                                                         |
| 50 | [Hypothesis Testing](#50-hypothesis-testing)                                                   |
| 51 | [Null &amp; Alternative Hypothesis](#51-null--alternative-hypothesis)                          |
| 52 | [Significance Level (α)](#52-significance-level-α)                                           |
| 53 | [Confidence Interval](#53-confidence-interval)                                                 |
| 54 | [Point Estimate](#54-point-estimate)                                                           |
| 55 | [Z-Test](#55-z-test)                                                                           |
| 56 | [T-Test](#56-t-test)                                                                           |
| 57 | [Z-Test vs T-Test](#57-z-test-vs-t-test)                                                       |
| 58 | [One-Tailed vs Two-Tailed Test](#58-one-tailed-vs-two-tailed-test)                             |
| 59 | [Z-Test for Proportion](#59-z-test-for-proportion)                                             |
| 60 | [Two-Proportion Z-Test](#60-two-proportion-z-test)                                             |
| 61 | [Chi-Square Test](#61-chi-square-test)                                                         |
| 62 | [ANOVA &amp; F-Test](#62-anova--f-test)                                                        |
| 63 | [Pareto Distribution](#63-pareto-distribution)                                                 |
| 64 | [Power Law Distribution](#64-power-law-distribution)                                           |
| 65 | [Log-Normal Distribution](#65-log-normal-distribution)                                         |
| 66 | [Box-Cox Transformation](#66-box-cox-transformation)                                           |
| 67 | [Missing Values &amp; Mean Imputation](#67-missing-values--mean-imputation)                    |
| 68 | [Outlier Detection Methods](#68-outlier-detection-methods)                                     |

---

## 1. What is Statistics

**What:**
Statistics is the science of collecting, organizing, analyzing, interpreting, and presenting data to make informed decisions.

**How:**
By applying mathematical methods to raw data — summarizing it, finding patterns, drawing conclusions, and making predictions.

**When:**
Every time you work with data — before modeling, during analysis, when reporting, when making business decisions.

**Why:**
Raw data alone tells no story. Statistics gives structure to chaos and makes data usable and trustworthy.

**General Example:**
You survey 100 people about their preferred ice cream flavor. Statistics helps you summarize responses, find the most popular flavor, and decide how much stock to order.

**Industry Example 1 — E-commerce:**
An online store collects 1 million transaction records. Statistics helps identify average order value, peak buying hours, most returned products, and seasonal trends — all driving inventory and marketing decisions.

**Industry Example 2 — Healthcare:**
A hospital tracks patient recovery times. Statistics determines whether a new drug actually reduces recovery time or if the improvement is just random chance.

---

## 2. Types of Statistics

**What:**
Two main branches: Descriptive (summarize) and Inferential (predict/conclude).

**How:**
Descriptive uses charts, averages, and spreads. Inferential uses probability, hypothesis tests, and confidence intervals.

**When:**
Descriptive when you want to describe what you have. Inferential when you want to draw conclusions beyond your sample.

**Why:**
Different questions require different tools. Mixing them leads to wrong conclusions.

**General Example:**
Class test scores — average and chart = Descriptive. Predicting how the entire school would score based on this class = Inferential.

**Industry Example 1 — Retail:**
Descriptive: "Average basket size this month was ₹1,200."
Inferential: "Based on this month's sample, we estimate 78% of customers nationwide will spend above ₹800."

**Industry Example 2 — HR:**
Descriptive: "Average employee tenure is 3.2 years."
Inferential: "We predict attrition will rise 12% next quarter based on engagement survey sample."

---

## 3. Descriptive Statistics

**What:**
Methods to summarize and describe the existing data you have — without making predictions.

**How:**
Using measures of central tendency (mean, median, mode), spread (variance, SD, range), and shape (skewness, kurtosis).

**When:**
First step of any analysis. Run descriptive stats before anything else.

**Why:**
You need to know what your data looks like before you can analyze it correctly.

**General Example:**
5 students scored: 60, 70, 75, 80, 90. Mean=75, Median=75, Range=30. This is descriptive stats.

**Industry Example 1 — Finance:**
A fund manager runs descriptive stats on 5 years of portfolio returns: mean return = 12%, SD = 4%, max = 22%, min = 3%. This gives a complete picture of performance without making predictions.

**Industry Example 2 — Manufacturing:**
QC team measures 500 bolts. Descriptive stats: mean diameter = 10.02mm, SD = 0.03mm, min = 9.95mm, max = 10.08mm. Identifies process consistency.

---

## 4. Inferential Statistics

**What:**
Using sample data to draw conclusions, make predictions, or test hypotheses about a larger population.

**How:**
Through hypothesis testing, confidence intervals, regression, and probability distributions.

**When:**
When you can't measure the entire population — which is almost always.

**Why:**
Collecting data from every individual is impossible. Inference lets you generalize from a sample.

**General Example:**
Survey 500 voters from a city of 2 million. Infer voting preference of the entire city.

**Industry Example 1 — Pharma:**
Test a drug on 300 patients. Use inferential stats to conclude whether the drug works for the entire patient population of millions.

**Industry Example 2 — EdTech:**
Survey 1,000 students about a new learning feature. Infer whether all 5 lakh platform users would find it helpful. Used to decide on full rollout.

---

## 5. Population vs Sample

**What:**
Population = entire group you want to study. Sample = subset you actually collect and analyze.

**How:**

```
Population Mean:  μ = Σx / N
Sample Mean:      x̄ = Σx / n

Population SD:    σ
Sample SD:        s
```

**When:**
Use population when you have complete data. Use sample (almost always) when you can only collect partial data.

**Why:**
Collecting data from every individual is usually impossible, too expensive, or too slow. Samples allow practical analysis.

**General Example:**
You want to know the average height of all Indians. Measuring 1.4 billion people = population. Measuring 10,000 people randomly = sample.

**Industry Example 1 — Banking:**
A bank wants to know the average loan default rate. Analyzing all 50 lakh loan accounts = population. Analyzing a random 10,000 accounts for a quick study = sample.

**Industry Example 2 — FMCG:**
Hindustan Unilever wants to know customer satisfaction. Surveying all 50 crore customers = impossible. Surveying 5,000 = sample used for inference.

---

## 6. Sampling Techniques

**What:**
Methods used to select a subset (sample) from a population.

**How:**

### Probability Sampling (Random — Less Bias)

| Technique               | How                                                  |
| ----------------------- | ---------------------------------------------------- |
| **Simple Random** | Every unit has equal chance of selection             |
| **Systematic**    | Every nth unit selected                              |
| **Stratified**    | Divide into subgroups, sample from each              |
| **Cluster**       | Divide into clusters, select whole clusters randomly |

### Non-Probability Sampling (May Have Bias)

| Technique             | How                                |
| --------------------- | ---------------------------------- |
| **Convenience** | Easiest to access                  |
| **Judgmental**  | Expert manually selects            |
| **Snowball**    | Existing subjects recruit new ones |
| **Quota**       | Fixed quotas per group             |

**When:**
Probability sampling when accuracy is critical. Non-probability when speed or access is the constraint.

**Why:**
The sampling method determines how representative your sample is — and therefore how valid your conclusions are.

**General Example:**
Picking names from a hat (simple random) vs. asking only your friends (convenience).

**Industry Example 1 — Market Research:**
FMCG company launching a new product. Uses stratified sampling — divides India into Urban/Semi-Urban/Rural, then randomly samples from each zone. Ensures all market segments are represented.

**Industry Example 2 — Quality Control:**
Factory produces 10,000 units daily. Uses systematic sampling — inspects every 50th unit off the production line. Efficient and still representative.

---

## 7. Variables & Types

**What:**
A variable is any characteristic or attribute that can take different values across observations.

**How:**

```
Variable
├── Qualitative (Categorical)
│   ├── Nominal  (No order)
│   └── Ordinal  (Has order)
└── Quantitative (Numerical)
    ├── Discrete  (Countable)
    └── Continuous (Measurable)
```

**When:**
Identifying variable type is the first step — it determines which statistical methods, charts, and tests are valid.

**Why:**
Using the wrong method for the wrong variable type gives meaningless or misleading results.

**General Example:**
Name = Nominal. Grade (A/B/C) = Ordinal. Number of children = Discrete. Height = Continuous.

**Industry Example 1 — HR Analytics:**
Employee dataset variables: Department (Nominal), Performance Rating (Ordinal), Number of Projects (Discrete), Salary (Continuous). Each requires different analysis methods.

**Industry Example 2 — E-commerce:**
Product category (Nominal), customer rating 1-5 (Ordinal), items in cart (Discrete), order value in ₹ (Continuous). Variable type determines which chart and test to apply.

---

## 8. Qualitative Data

**What:**
Data that represents categories or labels — not numbers. Cannot do arithmetic on it.

**How:**

**Nominal (No natural order):**

- Gender: Male / Female / Other
- Product type: Electronics / Clothing / Food
- Cannot rank meaningfully

**Ordinal (Has natural order):**

- Customer satisfaction: Poor < Fair < Good < Excellent
- Education: High School < Graduate < Post Graduate
- Can rank, but gaps between ranks are not equal

**When:**
Nominal for categories with no hierarchy. Ordinal when ranking or ordering matters.

**Why:**
Qualitative data captures attributes that numbers can't represent — identity, category, preference.

**General Example:**
Survey response "What is your favorite color?" = Nominal. "Rate this product 1-5 stars" = Ordinal.

**Industry Example 1 — Retail:**
Product returns categorized by reason: Defective / Wrong size / Changed mind (Nominal). Customer service rating: 1★ to 5★ (Ordinal). Both used in dashboard reporting.

**Industry Example 2 — Telecom:**
SIM type (Prepaid/Postpaid) = Nominal. Customer tier (Bronze/Silver/Gold/Platinum) = Ordinal. Ordinal tier directly affects discount slabs and retention strategies.

---

## 9. Quantitative Data

**What:**
Data that represents numeric values. Arithmetic operations (add, subtract, multiply) are meaningful.

**How:**

**Discrete:** Countable whole numbers. Cannot have decimals.
**Continuous:** Can take any value in a range — including decimals.

**When:**
Discrete for counts. Continuous for measurements.

**Why:**
Distinguishing discrete from continuous affects which probability distribution to use (Binomial vs Normal).

**General Example:**
Number of students in a class = Discrete (can't have 24.5 students). Height of students = Continuous (can be 165.7 cm).

**Industry Example 1 — Logistics:**
Number of packages delivered per day = Discrete. Delivery time in hours = Continuous. Used in route optimization and SLA tracking.

**Industry Example 2 — Banking:**
Number of transactions per customer per month = Discrete. Transaction amount in ₹ = Continuous. Both analyzed differently in fraud detection models.

---

## 10. Distribution

**What:**
Distribution describes how values of a variable are spread or arranged across a range — the shape of the data.

**How:**
Plot histogram → observe shape → identify distribution type.

```
Normal/Symmetric  →  Bell curve, Mean = Median = Mode
Right-skewed (+)  →  Long tail right, Mean > Median
Left-skewed (-)   →  Long tail left, Mean < Median
Uniform           →  All values equally likely
Bimodal           →  Two peaks
```

**When:**
Before any analysis. Distribution shape determines which measures and tests are valid.

**Why:**
Wrong assumption about distribution = wrong statistical test = wrong conclusions.

**General Example:**
Heights of 1,000 adults → roughly bell-shaped (normal). Income of 1,000 people → right-skewed (few very high earners).

**Industry Example 1 — Insurance:**
Claim amounts are right-skewed — most are small, few are extremely large. Using mean would overestimate the typical claim. Median used for pricing.

**Industry Example 2 — E-commerce:**
Page load times are right-skewed — most load in 1-2 seconds, but a few take 10+ seconds. Percentile analysis (P95, P99) used instead of mean for performance benchmarking.

---

## 11. Range

**What:**
The simplest measure of spread — the difference between maximum and minimum values.

**How:**

```
Range = Maximum − Minimum
```

**When:**
Quick first look at data spread. Not for detailed analysis.

**Why:**
Gives a rough sense of how wide the data is, but is easily distorted by outliers.

**General Example:**
Test scores: 45, 60, 70, 75, 95. Range = 95 − 45 = 50.

**Industry Example 1 — Finance:**
Stock price range over a year: High = ₹1,840, Low = ₹980. Range = ₹860. Used in volatility assessment and options pricing.

**Industry Example 2 — Manufacturing:**
Product weights: Min = 98g, Max = 104g. Range = 6g. If specification allows ±2g from 100g, this range indicates a process problem.

---

## 12. Histogram

**What:**
A bar chart for continuous/numerical data that shows the frequency distribution of values grouped into bins (ranges).

**How:**

```
X-axis  →  Bins (value ranges)
Y-axis  →  Frequency (count in each bin)
Bars    →  Touch each other (no gaps — unlike bar charts)
```

**When:**
During EDA to understand distribution shape, detect skewness, spot outliers, check normality.

**Why:**
Reveals the shape of your data visually — which drives all subsequent analysis decisions.

**General Example:**
Student marks grouped: 0-20, 20-40, 40-60, 60-80, 80-100. Bar height shows how many students scored in each range.

**Industry Example 1 — Banking:**
Histogram of loan amounts: most loans between ₹10K-₹25K, few above ₹1L. Right-skewed histogram → use median for reporting, not mean.

**Industry Example 2 — SaaS:**
Histogram of session durations: most users 1-5 minutes, long tail. Reveals that most users don't reach key features — drives UX redesign decision.

---

## 13. Mean

**What:**
The arithmetic average — sum of all values divided by count.

**How:**

```
Population Mean:  μ = Σx / N
Sample Mean:      x̄ = Σx / n
```

**When:**
Use when data is symmetric and has no extreme outliers.
Do NOT use when data is skewed or has outliers.

**Why:**
Mean is the most mathematically useful average — feeds into variance, SD, and most statistical tests. But it's sensitive to extreme values.

**General Example:**
Scores: 70, 75, 80, 85, 90. Mean = 400/5 = 80. Fair representation.
Scores: 70, 75, 80, 85, 500. Mean = 162. Now the mean is meaningless.

**Industry Example 1 — Retail:**
Average order value (AOV) calculated using mean for symmetric transaction data. Used in revenue forecasting and loyalty program design.

**Industry Example 2 — HR:**
Mean salary used to benchmark compensation when salaries are normally distributed within a band. But if one executive earns ₹5Cr and 99 staff earn ₹5L, mean is misleading — median used instead.

---

## 14. Median

**What:**
The middle value when data is sorted in ascending order.

**How:**

```
Odd count:  middle value directly
Even count: average of two middle values

Example (odd):  2, 4, 7, 9, 11  →  Median = 7
Example (even): 2, 4, 7, 9      →  Median = (4+7)/2 = 5.5
```

**When:**
Use when data is skewed, has outliers, or represents income/wealth/prices.

**Why:**
Median is not affected by extreme values — it always represents the "typical" middle observation.

**General Example:**
House prices in a neighborhood: ₹40L, ₹45L, ₹48L, ₹50L, ₹5Cr. Median = ₹48L. Mean = ₹1.57Cr. Median is the honest number.

**Industry Example 1 — Real Estate:**
Median property price used in all real estate reports because a few luxury properties would heavily inflate the mean. "Median home price rose 8%" is a meaningful headline.

**Industry Example 2 — Gig Economy:**
Median delivery time reported to customers because a few very delayed orders (due to storms, technical issues) would make the mean time look much worse than typical experience.

---

## 15. Mode

**What:**
The value that appears most frequently in the dataset.

**How:**

```
Find value with highest frequency.
Unimodal   →  one mode
Bimodal    →  two modes
Multimodal →  more than two
No mode    →  all values appear once
```

**When:**
Categorical/nominal data → mode is the ONLY valid central tendency measure.
Numerical data → use alongside mean and median.

**Why:**
Mode identifies the most common outcome — critical for inventory, sizing, product decisions.

**General Example:**
Shoe sizes sold: 7, 8, 8, 9, 9, 9, 10, 10. Mode = 9. Most popular size to stock.

**Industry Example 1 — Retail:**
Most ordered product SKU = Mode. Most common return reason = Mode. Drives replenishment and quality improvement priorities.

**Industry Example 2 — Telecom:**
Most common data plan chosen = Mode. Used to determine which plan to feature prominently in marketing and bundling offers.

---

## 16. Outlier

**What:**
A data point that is significantly different from the rest of the dataset — either extremely high or extremely low.

**How:**
Detection methods:

```
IQR Method:  Below Q1−1.5×IQR  OR  Above Q3+1.5×IQR
Z-Score:     |Z| > 3
Box Plot:    Points beyond whiskers
```

**When:**
During EDA, before modeling, before calculating mean or SD.

**Why:**
Outliers distort mean, variance, and SD. They can completely invalidate model training if not handled. But some outliers are genuinely important signals.

**General Example:**
Student scores: 60, 65, 70, 72, 68, 98. Score of 98 is an outlier — either exceptionally talented or data entry error.

**Industry Example 1 — Fraud Detection:**
A customer's typical transaction is ₹500-₹2000. A sudden ₹1,50,000 transaction is a statistical outlier → triggers fraud alert. Here the outlier is the signal.

**Industry Example 2 — ML Preprocessing:**
A dataset of employee salaries has one record showing ₹500Cr (data entry error). This outlier would shift the mean by lakhs and destroy model performance. Must be removed before training.

---

## 17. Dispersion

**What:**
Measures how spread out the values are around the center. Also called variability or spread.

**How:**
Two datasets can have the same mean but completely different spread:

```
Dataset A: 14, 15, 16  →  Mean=15, Low spread
Dataset B: 5,  15, 25  →  Mean=15, High spread
```

**When:**
After calculating central tendency — always pair mean with a measure of dispersion.

**Why:**
Mean alone is incomplete. Dispersion tells you how reliable and consistent the data is.

**General Example:**
Two cricket batsmen both average 50 runs. Player A scores 48-52 consistently. Player B scores 10 or 90 — same mean, very different reliability. Dispersion captures this.

**Industry Example 1 — Finance:**
Two mutual funds both return 12% annually on average. Fund A has SD=2% (consistent). Fund B has SD=15% (volatile). Dispersion reveals the risk.

**Industry Example 2 — Manufacturing:**
Two factories both produce parts averaging 10mm diameter. Factory A SD=0.01mm. Factory B SD=0.5mm. Factory B has quality consistency issues despite same mean.

---

## 18. Variance

**What:**
The average of squared differences from the mean. Measures how far values typically deviate from the mean.

**How:**

```
Population Variance:  σ² = Σ(xᵢ − μ)²  / N
Sample Variance:      s² = Σ(xᵢ − x̄)² / (n−1)

Why square?
→ Removes negatives (deviations cancel without squaring)
→ Penalizes larger deviations more heavily
```

**Step-by-step:**

```
Data: 2, 4, 6, 8
Mean = 5
Deviations:        -3, -1, +1, +3
Squared devs:       9,  1,  1,  9
Sum = 20
Sample Variance = 20/(4-1) = 6.67
```

**When:**
When you need a precise mathematical measure of spread. Input for Standard Deviation and many statistical tests.

**Why:**
Variance quantifies variability. Used in ANOVA, regression, portfolio theory, and most inferential methods.

**General Example:**
Test scores 70, 80, 90 have lower variance than 40, 80, 120. Same mean, very different spread.

**Industry Example 1 — Finance (Portfolio Theory):**
Portfolio variance measures total risk. Low variance = stable returns. Markowitz portfolio optimization minimizes variance while targeting a return level.

**Industry Example 2 — Operations:**
Call center tracks variance in call handling time. High variance = unpredictable staffing needs. Low variance = consistent, plannable operations.

---

## 19. Bessel's Correction & Degrees of Freedom

**What:**
Bessel's correction is the use of (n−1) instead of n in the sample variance formula to produce an unbiased estimate of population variance.

**How:**

```
Biased (wrong):   s² = Σ(xᵢ − x̄)² / n
Unbiased (right): s² = Σ(xᵢ − x̄)² / (n−1)  ← Bessel's Correction
```

**Degrees of Freedom:**

```
With n data points and 1 estimated parameter (mean):
→ Only (n−1) values are free to vary
→ The nth value is determined once mean and other (n−1) values are known
→ df = n−1
```

**When:**
Always use (n−1) when calculating sample variance or sample SD. Use N only for true population data.

**Why:**
Sample values cluster closer to sample mean (x̄) than to the true population mean (μ). This causes sample variance with divisor n to systematically underestimate σ². Dividing by (n−1) corrects this bias.

**General Example:**
4 values: 2, 4, 6, 8. Mean=5. If three values are 2,4,6 and mean=5, the 4th MUST be 8 — it's not free. df = 3 = n−1.

**Industry Example 1 — Quality Control:**
A sample of 25 products used to estimate population defect variance. Using (n−1)=24 in denominator ensures the estimate doesn't systematically understate the true process variability.

**Industry Example 2 — Data Science:**
`numpy.std(data, ddof=1)` and `numpy.var(data, ddof=1)` apply Bessel's correction. Default `ddof=0` gives population formula. Using wrong ddof in production code leads to underestimated variance — a common bug in junior analyst code.

---

## 20. Standard Deviation

**What:**
The square root of variance. Returns spread to the original unit of measurement.

**How:**

```
Population SD:  σ = √[Σ(xᵢ − μ)²  / N]
Sample SD:      s = √[Σ(xᵢ − x̄)² / (n−1)]

Mean ± 1SD contains roughly 68% of data (if normal)
```

**When:**
Whenever you report a mean, report SD alongside it. Used in Z-scores, control charts, model evaluation.

**Why:**
Variance is in squared units (₹², kg²) — hard to interpret. SD brings units back to original scale (₹, kg).

**General Example:**
Average exam score = 70, SD = 10. Typical student scores between 60-80. SD = 5 means everyone clustered tightly around 70.

**Industry Example 1 — Banking:**
Average EMI = ₹5,000, SD = ₹500. Typical borrower pays ₹4,500-₹5,500. High SD would indicate very diverse borrower profiles requiring different risk models.

**Industry Example 2 — SaaS Metrics:**
Average session duration = 4 minutes, SD = 0.5 minutes → consistent engagement. SD = 8 minutes → highly variable — some users engage deeply, most don't. Drives different product strategies.

---

## 21. Percentile

**What:**
A value below which a certain percentage of observations fall.

**How:**

```
Pₖ = k-th percentile
P50 = Median (50% below)
P25 = Q1     (25% below)
P75 = Q3     (75% below)
P90          (90% below)

Calculation:
Step 1: Sort ascending
Step 2: L = (k/100) × n
Step 3: If L whole → avg of Lth & (L+1)th values
        If L decimal → round up → value at that position
```

**When:**
For ranking, benchmarking, setting thresholds, understanding relative standing.

**Why:**
Percentiles give context to individual values — not just the absolute number but where it stands relative to the distribution.

**General Example:**
Scored 85/100 in a test. "What percentile?" = How many others scored below you? If P90, you beat 90% of candidates.

**Industry Example 1 — Education (NEET/CAT):**
A student at the 95th percentile scored higher than 95% of all test-takers. Percentile ranks are used over raw scores because they're standardized across different test difficulties.

**Industry Example 2 — Tech Performance:**
P99 latency = 200ms means 99% of requests are handled in under 200ms. SLAs are written in percentiles, not averages, because averages hide tail behavior that causes user complaints.

---

## 22. Quartiles & IQR

**What:**
Quartiles divide sorted data into 4 equal parts. IQR (Interquartile Range) measures the spread of the middle 50%.

**How:**

```
Q1 = P25  →  25% of data falls below
Q2 = P50  →  Median
Q3 = P75  →  75% of data falls below

IQR = Q3 − Q1

Outlier Fences:
Lower = Q1 − 1.5 × IQR
Upper = Q3 + 1.5 × IQR
Values outside fences = outliers
```

**When:**
During EDA, outlier detection, box plot construction, robust spread analysis.

**Why:**
IQR is robust — not affected by outliers (unlike range and SD). Describes the middle 50% of data.

**General Example:**
Salaries: Q1=₹30K, Q3=₹60K. IQR=₹30K. Anyone earning below ₹30K−1.5×₹30K=−₹15K (impossible) or above ₹60K+₹45K=₹105K is an outlier.

**Industry Example 1 — Healthcare:**
Patient waiting times: Q1=10min, Q3=35min, IQR=25min. Outlier fence = 35+1.5×25 = 72.5 minutes. Patients waiting >72.5 min flagged for service recovery.

**Industry Example 2 — E-commerce:**
Product delivery times: Q1=2 days, Q3=5 days, IQR=3 days. Outlier = >9.5 days. Outlier orders automatically escalated to customer support team.

---

## 23. Five-Number Summary

**What:**
A compact description of any dataset using exactly 5 key statistics.

**How:**

```
┌─────┬────┬────────┬────┬─────┐
│ Min │ Q1 │ Median │ Q3 │ Max │
└─────┴────┴────────┴────┴─────┘

IQR = Q3 − Q1
Range = Max − Min
```

**When:**
Quick complete picture of a dataset. First thing to check on any numerical column.

**Why:**
Five numbers capture center, spread, range, and potential outliers — everything needed for initial understanding.

**General Example:**

```
Exam scores: 45, 60, 70, 75, 80, 85, 95
Min=45, Q1=60, Median=75, Q3=85, Max=95
```

**Industry Example 1 — Sales:**
Monthly revenue five-number summary: Min=₹8L, Q1=₹15L, Median=₹22L, Q3=₹30L, Max=₹95L. Max far from Q3 suggests a one-time spike month — investigate before including in forecasts.

**Industry Example 2 — App Analytics:**
Daily active users: Min=1200, Q1=3500, Median=5000, Q3=6500, Max=22000. Max=22000 is an outlier (viral day). Median=5000 is the true daily typical.

---

## 24. Box Plot

**What:**
A visual representation of the Five-Number Summary — shows distribution, spread, skewness, and outliers in one chart.

**How:**

```
                   ┌──────────┬──────────┐
   ●         |─────┤   Box    │          ├─────|     ● ●
(outlier)  whisker  Q1       Q2         Q3   whisker (outliers)
                            (Median)

Whiskers extend to last value WITHIN fence (Q1±1.5×IQR)
Dots beyond whiskers = individual outliers
```

**Reading the shape:**

```
Median near center of box →  Symmetric
Median near Q1            →  Right-skewed
Median near Q3            →  Left-skewed
Long right whisker        →  High-end extreme values
Short box (small IQR)     →  Consistent, concentrated data
```

**When:**
EDA, comparing multiple groups, detecting outliers, understanding skewness.

**Why:**
One visual — five statistics + outliers + skewness + spread. Most information-dense single chart in statistics.

**General Example:**
Box plot of student scores: median=70, small box = class performed consistently. Long right whisker = a few very high scorers.

**Industry Example 1 — Operations:**
Box plots of delivery times for 5 logistics partners side by side. Immediately shows which partner is consistent vs. unpredictable. Used in vendor performance reviews.

**Industry Example 2 — Finance:**
Box plots of monthly returns for 10 investment schemes. Compact box = low volatility. Wide box or outlier dots = high-risk scheme. Used in fund comparison presentations.

---

## 25. Normal Distribution (Gaussian)

**What:**
A continuous probability distribution that forms a perfect bell-shaped, symmetric curve. Named after Carl Friedrich Gauss.

**How:**

```
Properties:
→ Mean = Median = Mode (all at center)
→ Symmetric around the mean
→ Total area under curve = 1 (100%)
→ Tails extend to ±∞, never touch x-axis
→ Defined by two parameters: μ (center) and σ (spread)

Formula:
f(x) = (1/σ√2π) × e^[−(x−μ)²/2σ²]

μ → shifts curve left/right
σ → controls width (large σ = flat/wide, small σ = tall/narrow)
```

**When:**
When data is symmetric and bell-shaped. Many statistical tests assume normality. Check before applying Z-test, t-test, or regression.

**Why:**
Most natural phenomena approximate normal distribution. It's the mathematical backbone of most classical statistics and many ML algorithms.

**General Example:**
Heights of 10,000 adults → bell curve centered around 5'7". Very few people are 4' or 7'. Most cluster around the average.

**Industry Example 1 — Manufacturing:**
Product weight coming off a production line follows normal distribution centered at 500g with SD=2g. Quality control uses this to set upper and lower control limits.

**Industry Example 2 — Finance:**
Daily stock returns approximately follow normal distribution. Risk models (VaR) use normality assumption to estimate probability of extreme losses.

---

## 26. Empirical Rule (68-95-99.7)

**What:**
For any normally distributed dataset, a fixed percentage of data falls within 1, 2, and 3 standard deviations of the mean.

**How:**

```
μ ± 1σ  →  68.27% of data
μ ± 2σ  →  95.45% of data
μ ± 3σ  →  99.73% of data
Beyond ±3σ → 0.27% (extremely rare → outlier zone)
```

**When:**
Setting outlier thresholds, quality control limits, risk bands, anomaly detection thresholds.

**Why:**
Provides instant probability estimates without needing the Z-table, as long as data is approximately normal.

**General Example:**

```
Employee salaries: μ = ₹50,000, σ = ₹8,000
68% earn: ₹42,000 to ₹58,000
95% earn: ₹34,000 to ₹66,000
99.7% earn: ₹26,000 to ₹74,000
Earning > ₹74K = statistical outlier
```

**Industry Example 1 — Manufacturing (Six Sigma):**
Six Sigma methodology uses 6σ (6 standard deviations) as the defect threshold. At ±3σ → 99.73% within spec → 2,700 defects per million. At ±6σ → 3.4 defects per million. Empirical rule is the foundation.

**Industry Example 2 — Cybersecurity:**
Network traffic volume: mean = 500GB/day, SD = 50GB. Alert triggers when traffic exceeds μ+3σ = 650GB (0.15% probability under normal conditions → likely an attack).

---

## 27. Standard Normal Distribution

**What:**
A special case of the normal distribution with mean = 0 and standard deviation = 1.

**How:**

```
Symbol: N(0, 1)
Mean = 0
SD   = 1

Any normal distribution → Standard Normal using Z-score:
Z = (x − μ) / σ
```

**When:**
Comparing values across different datasets. Looking up probabilities from Z-table. Standardizing features before ML models.

**Why:**
Different datasets have different μ and σ. Standard normal gives a universal reference scale for comparison and probability lookup.

**General Example:**
Student A scored 75 in Math (class avg=65, SD=10). Student B scored 82 in Science (class avg=75, SD=15). Who performed better relatively? Z-score answers this.

**Industry Example 1 — Recruitment:**
Aptitude test scores across 3 cities have different means and SDs. HR standardizes to Z-scores to compare candidates fairly across locations.

**Industry Example 2 — ML Preprocessing:**
Features in a dataset: Salary (₹lakhs), Age (years), Experience (months). StandardScaler converts all to Z-scores (mean=0, SD=1) so KNN, SVM, and Neural Networks treat them equally in distance calculations.

---

## 28. Z-Score

**What:**
A measure of how many standard deviations a value is from the mean.

**How:**

```
Z = (x − μ) / σ

Z = 0    →  Value equals the mean
Z = +1   →  1 SD above mean
Z = −1   →  1 SD below mean
Z > +3   →  Extreme high — potential outlier
Z < −3   →  Extreme low  — potential outlier
```

**When:**
Outlier detection, comparing values across different scales, standardizing features for ML, probability calculations.

**Why:**
Z-score provides context — not just how far a value is from the mean in raw units, but how unusual that distance is given the data's typical spread.

**General Example:**

```
Student A: Score=85, Class μ=70, SD=10
Z = (85−70)/10 = +1.5
→ Student A scored 1.5 standard deviations above class average
```

**Industry Example 1 — Finance (Altman Z-Score):**
Modified Z-score used to predict corporate bankruptcy risk. Companies with Z-score below 1.81 are in distress zone. Used by credit analysts globally.

**Industry Example 2 — Anomaly Detection:**
Website daily revenue: μ=₹5L, σ=₹50K. One day: ₹3L. Z=(3L−5L)/50K=−4. |Z|>3 → anomaly → trigger investigation. Was it a payment gateway outage? Marketing campaign failure?

---

## 29. Z-Table & Area Under Curve

**What:**
Z-table gives the cumulative probability (area under normal curve) to the LEFT of a given Z-score.

**How:**

```
Φ(Z) = Area to LEFT of Z (from Z-table)

Type 1 — P(X < a):   Area LEFT  = Φ(Z)
Type 2 — P(X > a):   Area RIGHT = 1 − Φ(Z)
Type 3 — P(a<X<b):   BETWEEN    = Φ(Z₂) − Φ(Z₁)

Key values:
Z = −2.0  →  Φ = 0.0228  (2.28% below)
Z = −1.0  →  Φ = 0.1587
Z =  0.0  →  Φ = 0.5000
Z = +1.0  →  Φ = 0.8413
Z = +2.0  →  Φ = 0.9772
Z = +3.0  →  Φ = 0.9987
```

**When:**
Finding probability of values falling in a range, hypothesis test p-values, confidence intervals.

**Why:**
Converts Z-scores to probabilities — the language of statistical decision-making.

**General Example:**

```
IQ: μ=100, σ=15. P(IQ < 115)?
Z = (115−100)/15 = +1.0
Φ(1.0) = 0.8413 → 84.13% of people have IQ below 115
```

**Industry Example 1 — Insurance:**
Claim amount: μ=₹50K, σ=₹10K. P(claim > ₹70K)?
Z=(70-50)/10=2.0 → P(X>70K) = 1−0.9772 = 2.28%. Used in reserve calculation.

**Industry Example 2 — Quality Control:**
Product length: μ=10cm, σ=0.1cm. Spec: 9.8 to 10.2cm.
Z₁=(9.8-10)/0.1=−2, Z₂=(10.2-10)/0.1=+2
P(in spec) = Φ(2)−Φ(−2) = 0.9772−0.0228 = 95.44%.

---

## 30. Central Limit Theorem (CLT)

**What:**
Regardless of the shape of the population distribution, the distribution of sample means approaches normal distribution as sample size increases — provided n ≥ 30.

**How:**

```
Population (any shape — skewed, bimodal, uniform)
     ↓
Take many samples of size n ≥ 30
     ↓
Calculate mean of each sample
     ↓
Plot all sample means
     ↓
Result = Normal Distribution!
Center = μ (population mean)
Spread = σ/√n (Standard Error)
```

**When:**
Justifying use of normal-based tests on non-normal population data. Building confidence intervals. Running hypothesis tests on real-world messy data.

**Why:**
Real-world data is almost never perfectly normal. CLT is what makes statistical inference possible on messy real data. It's the theoretical foundation of most inferential statistics.

**General Example:**
Roll a die (uniform distribution). Average of 1 roll = anywhere 1-6. Average of 30 rolls = approximately 3.5 (normally distributed around the true mean).

**Industry Example 1 — Consumer Research:**
Customer satisfaction scores are heavily skewed (most give 4-5 stars, few give 1-2). Despite this, sample mean satisfaction from 200 customers is normally distributed → enables hypothesis testing and confidence intervals.

**Industry Example 2 — Operations:**
Daily delivery times follow a skewed distribution. CLT allows the operations team to build confidence intervals around mean delivery time using 50+ daily observations, enabling SLA commitments.

---

## 31. Standard Error

**What:**
The standard deviation of the sampling distribution of the sample mean. Measures how much the sample mean varies from sample to sample.

**How:**

```
SE = σ / √n

As n increases → SE decreases → sample means cluster closer to μ
Larger sample = more reliable = more precise estimate
```

**When:**
Building confidence intervals, hypothesis tests, comparing sample means.

**Why:**
SE quantifies the precision of the sample mean as an estimator of the population mean.

**General Example:**
σ=10, n=100 → SE = 10/√100 = 1. SE=1 means sample means vary by only ±1 on average. n=25 → SE=2 (less precise).

**Industry Example 1 — Clinical Trial:**
Drug trial with n=400 patients. SE of mean recovery time = σ/20. Larger trial → smaller SE → more confident estimate of true population recovery time.

**Industry Example 2 — Survey Design:**
Market research firm calculates SE to determine required sample size. Target SE = ₹50 on a mean estimate → SE=σ/√n → n=(σ/50)². Pre-determines sample size before fieldwork.

---

## 32. Basic Probability

**What:**
The measure of likelihood that an event will occur. Always between 0 and 1.

**How:**

```
P(Event) = Favorable outcomes / Total outcomes

P(impossible) = 0
P(certain)    = 1
P(A) + P(A')  = 1   ← Complement rule
```

**When:**
Anytime you need to quantify uncertainty or likelihood of an outcome.

**Why:**
Probability is the language of uncertainty. All of statistics and ML is built on probabilistic thinking.

**General Example:**
Rolling a die: P(getting 4) = 1/6 ≈ 0.167. P(getting even) = 3/6 = 0.5.

**Industry Example 1 — Insurance:**
P(a 35-year-old male making a health claim in a year) = historical claims/total 35-year-old males. Used in premium calculation.

**Industry Example 2 — E-commerce:**
P(customer returns a product) = returns/total orders = 0.08 (8%). Used in reverse logistics planning and refund provisioning.

---

## 33. Bernoulli Distribution

**What:**
A distribution with exactly two outcomes: Success (1) or Failure (0). Models a single trial.

**How:**

```
P(X=1) = p      ← success probability
P(X=0) = 1 − p  ← failure probability

Mean     = p
Variance = p(1−p) = pq
```

**When:**
Any single binary outcome — click/no-click, default/no-default, defective/not-defective.

**Why:**
Building block of Binomial distribution. Foundation for logistic regression, which predicts Bernoulli probabilities.

**General Example:**
Flipping a fair coin: P(Heads)=0.5, P(Tails)=0.5. Mean=0.5, Variance=0.25.

**Industry Example 1 — Credit Risk:**
Will this customer default? Yes(1) or No(0). P(default)=0.03 based on credit history. Each customer = one Bernoulli trial. Logistic regression models P(default).

**Industry Example 2 — Digital Marketing:**
User clicks on an ad: Click(1) or No Click(0). CTR (click-through rate) = p in the Bernoulli model. A/B test compares p of two ad versions.

---

## 34. Binomial Distribution

**What:**
Distribution of the number of successes in n independent Bernoulli trials with constant probability p.

**How:**

```
P(X = k) = ⁿCₖ × pᵏ × (1−p)^(n−k)

k = number of successes
n = total trials
p = P(success) per trial

Mean     = n × p
Variance = n × p × (1−p)
SD       = √[n × p × (1−p)]

Conditions:
1. Fixed n trials
2. Two outcomes per trial
3. Constant p
4. Independent trials

Normal approximation valid when: np ≥ 5 AND n(1−p) ≥ 5
```

**When:**
Counting successes in a fixed number of trials. Quality inspection, survey yes/no questions, conversion counts.

**Why:**
Models the most common business scenario — how many successes will we get out of n attempts?

**General Example:**
Manufacturing: P(defective)=0.02. Inspect 100 units. P(exactly 3 defective)?
= ¹⁰⁰C₃ × (0.02)³ × (0.98)⁹⁷ ≈ 18.2%

**Industry Example 1 — Sales:**
Cold call conversion rate = 10%. Salesperson makes 20 calls per day.
P(at least 3 conversions) = 1 − P(0) − P(1) − P(2). Used to set realistic daily targets.

**Industry Example 2 — Quality Control:**
10,000 units produced daily, 1% defect rate. Expected defects = np = 100. SD = √(10000×0.01×0.99) ≈ 9.95. Control limits set at mean ± 3SD.

---

## 35. Mutually Exclusive Events

**What:**
Two events that cannot happen simultaneously — if one occurs, the other cannot.

**How:**

```
P(A ∩ B) = 0   (no overlap)
P(A ∪ B) = P(A) + P(B)
```

**When:**
Categorical outcomes where only one can occur at a time.

**Why:**
Allows simple addition of probabilities. Misidentifying events as mutually exclusive when they're not leads to probability errors.

**General Example:**
Rolling a die: Getting 3 AND getting 5 on the same roll = impossible. Mutually exclusive.

**Industry Example 1 — Telecom:**
A customer can only be on one plan: Prepaid OR Postpaid. These are mutually exclusive. P(prepaid or postpaid) = P(prepaid) + P(postpaid).

**Industry Example 2 — Insurance:**
A single claim can be classified as either Fire OR Flood OR Theft — not multiple (in a single-cause policy). Mutually exclusive categories simplify actuarial calculations.

---

## 36. Non-Mutually Exclusive Events

**What:**
Events that can occur simultaneously — there is overlap between them.

**How:**

```
P(A ∪ B) = P(A) + P(B) − P(A ∩ B)
           (subtract overlap to avoid double-counting)
```

**When:**
When two events can co-occur and their intersection has nonzero probability.

**Why:**
Failing to subtract overlap leads to overestimated probability.

**General Example:**
Drawing a card: P(King) = 4/52, P(Heart) = 13/52, P(King of Hearts) = 1/52.
P(King OR Heart) = 4/52 + 13/52 − 1/52 = 16/52 ≈ 0.308.

**Industry Example 1 — Marketing:**
P(customer buys Product A) = 0.3, P(customer buys Product B) = 0.4, P(buys both) = 0.15.
P(buys A or B) = 0.3 + 0.4 − 0.15 = 0.55. Used in cross-sell revenue estimation.

**Industry Example 2 — HR:**
P(employee in Tech) = 0.35, P(employee with MBA) = 0.20, P(Tech AND MBA) = 0.08.
P(Tech OR MBA) = 0.35 + 0.20 − 0.08 = 0.47. Used in talent segmentation.

---

## 37. Addition Rule

**What:**
Formula for finding the probability of at least one of two events occurring.

**How:**

```
Mutually Exclusive:
P(A ∪ B) = P(A) + P(B)

Non-Mutually Exclusive (General Rule):
P(A ∪ B) = P(A) + P(B) − P(A ∩ B)
```

**When:**
Finding probability of "A OR B" happening.

**Why:**
Ensures probabilities are correctly calculated without double-counting.

**General Example:**
P(Rain) = 0.4, P(Traffic) = 0.3, P(Rain AND Traffic) = 0.15.
P(Rain OR Traffic) = 0.4 + 0.3 − 0.15 = 0.55.

**Industry Example 1 — Risk Management:**
P(Server A fails) = 0.05, P(Server B fails) = 0.03, P(both fail) = 0.001.
P(at least one fails) = 0.05 + 0.03 − 0.001 = 0.079. Used in uptime SLA planning.

**Industry Example 2 — Retail:**
P(customer uses coupon) = 0.25, P(customer is a loyalty member) = 0.40, P(both) = 0.12.
P(coupon OR loyalty) = 0.53. Helps estimate which customers need marketing outreach.

---

## 38. Independent Events

**What:**
Events where occurrence of one does NOT affect the probability of the other.

**How:**

```
P(A ∩ B) = P(A) × P(B)

Verification: P(B|A) = P(B)  → A gives no information about B
```

**When:**
Separate trials with no connection. Coin tosses, dice rolls, independent customer decisions.

**Why:**
Independence simplifies probability calculation — just multiply. Assuming independence when events are actually dependent is a serious modeling error.

**General Example:**
Tossing two coins: P(HH) = 0.5 × 0.5 = 0.25. First toss doesn't affect second.

**Industry Example 1 — A/B Testing:**
Two users independently see different versions of a webpage. Their purchase decisions are independent. P(both purchase) = P(A purchases) × P(B purchases).

**Industry Example 2 — Manufacturing:**
Two machines operating independently. P(Machine 1 fails) = 0.02, P(Machine 2 fails) = 0.03.
P(both fail simultaneously) = 0.02 × 0.03 = 0.0006. Used in redundancy planning.

---

## 39. Dependent Events

**What:**
Events where occurrence of one changes the probability of the other.

**How:**

```
P(A ∩ B) = P(A) × P(B|A)

P(B|A) = conditional probability of B given A occurred
```

**When:**
Sampling WITHOUT replacement. Sequential decisions. Any case where first outcome changes the remaining pool.

**Why:**
Ignoring dependence leads to underestimated or overestimated probabilities — common error in real problems.

**General Example:**
Bag with 3 Red, 2 Blue marbles.
P(Red 1st) = 3/5. P(Red 2nd | Red 1st) = 2/4 (bag now has 4 marbles, 2 red).
P(Both Red) = 3/5 × 2/4 = 0.30.

**Industry Example 1 — Hiring:**
5 candidates for 2 positions. P(Candidate A selected) = 1/5. Given A selected, P(B selected) = 1/4.
P(A AND B both selected) = 1/5 × 1/4 = 1/20. Interview scheduling logic uses this.

**Industry Example 2 — Fraud Detection:**
Fraudulent transaction cluster: P(2nd transaction is fraud | 1st was fraud) >> P(fraud) in general. Dependency between consecutive suspicious transactions used in sequential fraud detection models.

---

## 40. Multiplication Rule

**What:**
Formula for the probability of two events both occurring.

**How:**

```
Independent events:  P(A ∩ B) = P(A) × P(B)
Dependent events:    P(A ∩ B) = P(A) × P(B|A)
```

**When:**
Finding P(A AND B) — both events happening.

**Why:**
The most fundamental rule for calculating joint probabilities in both simple and complex systems.

**General Example:**
P(rain) = 0.4, P(traffic | rain) = 0.7.
P(rain AND traffic) = 0.4 × 0.7 = 0.28.

**Industry Example 1 — Supply Chain:**
P(supplier delivers on time) = 0.90. P(production runs on schedule | supplier on time) = 0.85.
P(both) = 0.90 × 0.85 = 0.765. Used in delivery commitment calculations.

**Industry Example 2 — Cybersecurity:**
P(phishing email opened) = 0.30. P(malware installed | email opened) = 0.25.
P(malware installed) = 0.30 × 0.25 = 0.075. Used in security training ROI analysis.

---

## 41. Conditional Probability

**What:**
The probability of event B occurring given that event A has already occurred.

**How:**

```
P(B|A) = P(A ∩ B) / P(A)

Read as: "Probability of B given A"
```

**When:**
When prior information changes the probability of an outcome. Bayesian reasoning, sequential decisions, recommendation systems.

**Why:**
Most real-world probabilities are conditional — context always matters. Foundation of Bayes' Theorem, Naive Bayes classifier, and medical diagnosis.

**General Example:**
P(it rains) = 0.3. P(ground is wet) = 0.4. P(ground wet AND rain) = 0.25.
P(rain | ground is wet) = 0.25/0.4 = 0.625. Given wet ground, 62.5% chance it rained.

**Industry Example 1 — Healthcare:**
P(disease) = 0.01. P(positive test | disease) = 0.95. P(positive test | no disease) = 0.05.
P(disease | positive test) = Bayes → about 16%. A positive test doesn't mean 95% chance of disease.
Critical for medical decision-making.

**Industry Example 2 — E-commerce:**
P(customer buys again | already bought once) >> P(customer buys generally). Email retention campaigns target customers conditional on prior purchase behavior.

---

## 42. Permutation

**What:**
The number of ways to arrange items where ORDER MATTERS.

**How:**

```
ⁿPᵣ = n! / (n − r)!

n = total items
r = items being arranged
! = factorial (5! = 5×4×3×2×1 = 120)

Example: ⁵P₃ = 5!/(5-3)! = 120/2 = 60
```

**When:**
Rankings, sequences, passwords, race positions — anywhere order changes the outcome.

**Why:**
Counting arrangements is fundamental to probability calculation for ordered selection problems.

**General Example:**
How many ways can 3 books be arranged on a shelf from a collection of 7?
⁷P₃ = 7!/(7-3)! = 7×6×5 = 210 ways.

**Industry Example 1 — HR:**
8 candidates interviewing for 3 ranked positions (1st choice, 2nd, 3rd).
⁸P₃ = 8×7×6 = 336 possible ranking combinations. Used in structured hiring matrix design.

**Industry Example 2 — Cryptography:**
4-digit PIN from 0-9, no repetition.
¹⁰P₄ = 10×9×8×7 = 5,040 possible PINs. Used in security policy design for minimum PIN complexity.

---

## 43. Combination

**What:**
The number of ways to select items where ORDER DOES NOT MATTER.

**How:**

```
ⁿCᵣ = n! / (r! × (n − r)!)

Example: ⁵C₃ = 5!/(3!×2!) = 120/12 = 10
```

**When:**
Team selection, lottery, choosing features — anywhere the group matters but not the order.

**Why:**
Combinations count selections, not arrangements. Gives smaller counts than permutations (since AB = BA in combinations).

**General Example:**
Choose 3 pizza toppings from 8 options.
⁸C₃ = 8!/(3!×5!) = 56 possible combinations.

**Industry Example 1 — Data Science:**
Selecting 5 features from 20 for a model.
²⁰C₅ = 15,504 possible feature subsets. Basis for exhaustive feature selection strategies.

**Industry Example 2 — Lottery & Gaming:**
Lottery: choose 6 numbers from 49.
⁴⁹C₆ = 13,983,816 combinations. P(winning) = 1/13,983,816. Used in prize pool design and expected value calculations.

---

## 44. Covariance

**What:**
Measures the direction of the linear relationship between two variables — whether they tend to move together (positive) or in opposite directions (negative).

**How:**

```
Population: Cov(X,Y) = Σ[(xᵢ−μₓ)(yᵢ−μᵧ)] / N
Sample:     Cov(X,Y) = Σ[(xᵢ−x̄)(yᵢ−ȳ)] / (n−1)

Cov > 0  →  X and Y move in same direction
Cov < 0  →  X and Y move in opposite directions
Cov = 0  →  No linear relationship

Special case: Cov(X, X) = Variance(X)
```

**When:**
Understanding relationships between two variables. Input to Pearson correlation and PCA.

**Why:**
Reveals direction of association. But it's unit-dependent — can't compare across different datasets. Correlation fixes this.

**Worked Example:**

```
Hours (X): 2,  4,  6,  8   →  x̄ = 5
Score (Y):50, 60, 75, 85   →  ȳ = 67.5

Σ[(x−x̄)(y−ȳ)] = (−3×−17.5)+(−1×−7.5)+(1×7.5)+(3×17.5) = 120
Cov = 120/(4−1) = 40  →  Positive relationship
```

**Industry Example 1 — Finance:**
Covariance between two stocks used in portfolio optimization. Positive covariance = both fall together (risky). Negative covariance = diversification benefit.

**Industry Example 2 — Marketing:**
Covariance between ad spend and sales revenue. Positive = increasing ad spend associates with increased revenue. Foundation for marketing mix models.

---

## 45. Pearson Correlation

**What:**
Normalized covariance that measures the direction AND strength of a LINEAR relationship between two continuous variables. Always between −1 and +1.

**How:**

```
r = Cov(X,Y) / (σₓ × σᵧ)

r = +1  →  Perfect positive linear relationship
r =  0  →  No linear relationship
r = −1  →  Perfect negative linear relationship

Strength interpretation:
|r| ≥ 0.9 → Very strong
|r| ≥ 0.7 → Strong
|r| ≥ 0.5 → Moderate
|r| ≥ 0.3 → Weak
|r| < 0.3 → Very weak/negligible
```

**When:**
Continuous, normally distributed data with a linear relationship. No significant outliers.

**Why:**
Pearson gives a standardized, interpretable measure of linear association. Used in feature selection, EDA, and as input to regression.

**General Example:**
r = 0.87 between study hours and exam scores → strong positive relationship. More study → more marks, consistently.

**Industry Example 1 — Real Estate:**
r = 0.82 between house size (sq ft) and price. Strong positive. Used to validate that size is a good predictor before building a price prediction model.

**Industry Example 2 — Feature Selection (ML):**
Compute Pearson correlation between all features and target variable. Keep features with |r| > 0.3 with target. Remove features with |r| > 0.85 with each other (multicollinearity). Reduces model complexity.

---

## 46. Spearman Rank Correlation

**What:**
Rank-based correlation that measures the direction and strength of a MONOTONIC relationship (not necessarily linear). More robust than Pearson.

**How:**

```
Step 1: Convert both variables to ranks
Step 2: Calculate rank difference d for each pair
Step 3: Apply formula:

rₛ = 1 − [6 × Σd²] / [n(n²−1)]

d = difference in ranks for each pair
n = number of observations
```

**Worked Example:**

```
Student  Hours  Rank_X  Score  Rank_Y   d    d²
A          2       1      50      1      0     0
B          4       2      65      3     −1     1
C          6       3      60      2     +1     1
D          8       4      85      4      0     0

Σd² = 2, n = 4
rₛ = 1 − [6×2]/[4×15] = 1 − 12/60 = 0.80
```

**When:**
Ordinal data, skewed distributions, outliers present, non-linear but monotonic relationships.

**Why:**
Spearman is robust — based on ranks, not raw values. Outliers don't distort it. Works even when Pearson's normality assumption is violated.

**Industry Example 1 — HR:**
Ranking employees by performance score (ordinal) and correlating with retention probability (ordinal). Spearman appropriate since both are rank-based.

**Industry Example 2 — E-commerce:**
Correlate product price rank with sales rank. Spearman used because price data is skewed (few very expensive products) and outliers are common.

---

## 47. Pearson vs Spearman

**What:**
Two different correlation measures — choosing the right one prevents misleading analysis.

**How:**

| Feature             | Pearson            | Spearman            |
| ------------------- | ------------------ | ------------------- |
| Data type           | Continuous, normal | Ordinal or any      |
| Relationship        | Linear only        | Monotonic           |
| Outlier sensitivity | High ✗            | Low ✓              |
| Based on            | Raw values         | Ranks               |
| Formula             | Cov/σₓσᵧ       | 1−6Σd²/n(n²−1) |

```
Decision:
Normal + Linear + Clean data  →  Pearson
Skewed / Ordinal / Outliers   →  Spearman
Non-linear monotonic           →  Spearman
When in doubt                  →  Spearman (safer)
```

**When:**
Start with Pearson. If normality or linearity is violated → switch to Spearman.

**Why:**
Using Pearson on skewed data or data with outliers gives misleading correlation values.

**General Example:**
Income vs. spending → Income is skewed → Use Spearman. Height vs. weight (normally distributed) → Pearson.

**Industry Example 1 — Banking:**
Loan amount (skewed, has outliers) vs. default probability → Spearman.
Credit score (approximately normal) vs. interest rate → Pearson.

**Industry Example 2 — Supply Chain:**
Delivery rank vs. customer satisfaction rank → Spearman.
Order volume vs. revenue (continuous, linear) → Pearson.

---

## 48. Feature Selection Using Correlation

**What:**
Using correlation analysis to identify which features are relevant to include in a model and which to remove.

**How:**

```
Step 1: Build correlation matrix of all features + target
Step 2: Remove multicollinearity:
        |r| > 0.85 between two features → drop one
Step 3: Remove irrelevant features:
        |r| < 0.1 with target → candidate for removal
Step 4: Visualize with heatmap
```

**When:**
Before training any ML model. During EDA to reduce dimensionality.

**Why:**
Irrelevant features add noise. Correlated features (multicollinearity) distort regression coefficients and make models unstable.

**General Example:**
Features: Age, Income, Years_Employed. Age and Years_Employed have r=0.92 → remove one before regression.

**Industry Example 1 — Credit Scoring:**
15 financial features correlated with default. Keep 8 with |r|>0.2 to target. Remove 3 pairs with |r|>0.85 between them. Model accuracy improves and is more interpretable for regulatory requirements.

**Industry Example 2 — Marketing Mix Modeling:**
Correlation matrix of marketing channels (TV, Digital, Radio, OOH) vs. sales. Channels with near-zero correlation to sales removed. Collinear channels (TV and Radio often correlated) handled via VIF or dropping one.

---

## 49. P-Value

**What:**
The probability of obtaining results at least as extreme as observed, assuming the null hypothesis is true.

**How:**

```
p-value = P(result this extreme OR more | H₀ is true)

p < α   →  Reject H₀  (result is unlikely under H₀)
p ≥ α   →  Fail to Reject H₀

Common thresholds:
p < 0.01  →  Very strong evidence against H₀
p < 0.05  →  Strong evidence (standard threshold)
p < 0.10  →  Weak evidence
p > 0.10  →  Insufficient evidence
```

**When:**
Every hypothesis test produces a p-value. Used to make reject/fail-to-reject decisions.

**Why:**
P-value translates a test statistic into a probability — making statistical decisions interpretable and standardized.

**General Example:**
Toss a coin 100 times, get 65 heads. If the coin were fair, p-value = P(≥65 heads by chance). If p < 0.05 → coin is likely biased.

**Industry Example 1 — A/B Testing:**
New webpage design tested. Conversion rate: Control=4.2%, Test=4.7%. p-value=0.03 < 0.05 → Reject H₀ → New design significantly better → Roll out.

**Industry Example 2 — Pharma:**
Clinical trial: new drug vs. placebo. p-value = 0.001 → Extremely strong evidence drug works. p-value = 0.12 → Insufficient evidence → More trials needed before approval.

---

## 50. Hypothesis Testing

**What:**
A formal statistical method to decide whether sample evidence supports or contradicts a claim about a population.

**How:**

```
Step 1: State H₀ (null) and H₁ (alternative)
Step 2: Choose significance level α (usually 0.05)
Step 3: Select appropriate test
Step 4: Calculate test statistic
Step 5: Find p-value or compare to critical value
Step 6: Decision — Reject or Fail to Reject H₀
Step 7: Interpret in business context
```

**When:**
Comparing groups, testing claims, validating before decisions, A/B testing, quality audits.

**Why:**
Without hypothesis testing, we'd act on differences that are just random noise. Hypothesis testing separates signal from chance.

**General Example (Coin):**
Claim: Coin is fair. Toss 100 times, get 65 heads.
H₀: P(H)=0.5. H₁: P(H)≠0.5.
Calculate Z → find p → compare to 0.05 → decide.

**Industry Example 1 — Operations:**
Manager claims average processing time = 10 minutes. Team samples 40 orders: mean=11.2 minutes. Hypothesis test determines if this difference is statistically significant or just sampling variation.

**Industry Example 2 — Product:**
Is the new onboarding flow better? H₀: completion rates are equal. H₁: new flow has higher completion. Run test on 1,000 users per variant. Hypothesis test gives statistical evidence for/against shipping.

---

## 51. Null & Alternative Hypothesis

**What:**
H₀ (Null) = default assumption, status quo, no effect.
H₁ (Alternative) = what we're trying to prove, opposite of H₀.

**How:**

```
H₀: Always contains equality (=, ≤, ≥)
H₁: Always contains inequality (≠, <, >)

Examples:
H₀: μ = 50    H₁: μ ≠ 50  (two-tailed)
H₀: μ = 50    H₁: μ > 50  (right-tailed)
H₀: μ = 50    H₁: μ < 50  (left-tailed)

NEVER "Accept H₀" — only Reject or Fail to Reject
```

**When:**
Before every hypothesis test. Hypotheses must be stated before data collection.

**Why:**
Clear hypotheses prevent bias — they commit you to a decision rule before seeing the data.

**General Example:**
Drug trial: H₀: drug has no effect. H₁: drug reduces blood pressure. We try to disprove H₀.

**Industry Example 1 — Marketing:**
H₀: Email subject line A and B have equal open rates.
H₁: Subject line B has higher open rate.
Run test on 5,000 subscribers each. Decision drives which line goes to full list.

**Industry Example 2 — Quality:**
H₀: Defect rate = 2% (standard).
H₁: Defect rate > 2% (process problem).
Sample 500 units. Test at α=0.05. Reject H₀ → halt production, investigate.

---

## 52. Significance Level (α)

**What:**
The threshold set BEFORE testing — the maximum acceptable probability of wrongly rejecting a true H₀ (Type I error rate).

**How:**

```
Most common: α = 0.05

Confidence Level = 1 − α

α = 0.10 → 90% confidence
α = 0.05 → 95% confidence  ← standard
α = 0.01 → 99% confidence  ← medical, legal

Rule: if p-value < α → Reject H₀
      if p-value ≥ α → Fail to Reject H₀
```

**When:**
Set before running any test. Never adjust after seeing results (p-hacking).

**Why:**
α defines how much evidence is needed to reject H₀. Lower α = more strict = less likely to make false positive errors.

**General Example:**
α=0.05 means: if H₀ is actually true, there is only a 5% chance our sample would produce results this extreme by random chance.

**Industry Example 1 — Pharma:**
FDA requires α=0.01 for drug approval (99% confidence). Higher standard because wrong approval (Type I error) could harm patients.

**Industry Example 2 — Tech (A/B Testing):**
Most product teams use α=0.05. Some use α=0.10 for quick exploratory tests where speed matters more than certainty.

---

## 53. Confidence Interval

**What:**
A range of values within which the true population parameter is likely to lie, with a specified confidence level.

**How:**

```
CI = x̄ ± Z* × (σ/√n)    [σ known]
CI = x̄ ± t* × (s/√n)    [σ unknown]

Critical Z* values:
90% CI → Z* = 1.645
95% CI → Z* = 1.960
99% CI → Z* = 2.576

Lower Limit = x̄ − Z* × SE
Upper Limit = x̄ + Z* × SE
SE = σ/√n
```

**Correct interpretation:**
"If we repeated this sampling 100 times, approximately 95 intervals would contain the true μ."
NOT: "95% probability the true μ is in this specific interval."

**When:**
Estimating population parameters, reporting survey results, clinical trials, setting SLAs.

**Why:**
Point estimates give false precision. CI acknowledges uncertainty honestly — essential for responsible reporting.

**General Example:**
Survey of 200 people: x̄=₹45,000 monthly income, σ=₹8,000.
95% CI = 45,000 ± 1.96×(8000/√200) = ₹43,891 to ₹46,109.

**Industry Example 1 — Market Research:**
"We are 95% confident the true market adoption rate is between 23% and 31%." Used in investor presentations and go/no-go decisions.

**Industry Example 2 — Clinical Trial:**
Mean recovery time: 8.5 days, 95% CI: [7.2, 9.8]. If CI doesn't include the standard treatment's 10 days → new drug is significantly better.

---

## 54. Point Estimate

**What:**
A single value used as the best guess for an unknown population parameter.

**How:**

```
x̄  →  estimates  μ  (population mean)
s   →  estimates  σ  (population SD)
p̂  →  estimates  P  (population proportion)
```

**When:**
When a single summary number is needed. Always pair with CI for honest reporting.

**Why:**
Point estimate is useful but incomplete — CI adds the crucial context of uncertainty.

**General Example:**
"Average delivery time is 3.2 days" = point estimate. Better: "3.2 days, 95% CI: [2.9, 3.5 days]."

**Industry Example 1 — Operations:**
Fleet GPS data gives point estimate of average fuel efficiency = 14.2 km/L. Used as baseline for planning fuel budgets before CI is needed.

**Industry Example 2 — HR:**
HR survey: 72% of employees satisfied (point estimate). Board presentation includes 95% CI [68%, 76%] to convey measurement precision.

---

## 55. Z-Test

**What:**
A hypothesis test using the standard normal distribution to test a claim about a population mean (or proportion) when σ is known or n ≥ 30.

**How:**

```
Formula (mean):       Z = (x̄ − μ₀) / (σ/√n)
Formula (proportion): Z = (p̂ − p₀) / √[p₀(1−p₀)/n]

Conditions:
→ σ known  →  Z-test (any n)
→ n ≥ 30   →  Z-test (even if σ unknown)
```

**When:**
Large samples or known population SD. Marketing campaigns, operations metrics, proportion tests.

**Why:**
Simpler than t-test when conditions are met. Well-established and widely accepted in industry.

**General Example:**

```
Claim: μ = 500g. Sample n=50, x̄=492g, σ=20g, α=0.05.
Z = (492−500)/(20/√50) = −8/2.83 = −2.83
|Z| = 2.83 > 1.96 → Reject H₀
```

**Industry Example 1 — Manufacturing:**
Bolt length claim: μ=50mm, σ=2mm. Sample n=40, x̄=49.2mm.
Z=(49.2−50)/(2/√40)=−2.53. p=0.006 < 0.05 → Machine under-producing → maintenance.

**Industry Example 2 — Telecom:**
Claim: Average call duration = 4.5 minutes. Customer sample n=100, x̄=4.1 min, σ=1.2 min.
Z=(4.1−4.5)/(1.2/10)=−3.33. Reject H₀. Call times significantly shorter — impacts billing model.

---

## 56. T-Test

**What:**
A hypothesis test using the t-distribution when σ is unknown — especially for small samples (n < 30).

**How:**

```
Formula: t = (x̄ − μ₀) / (s/√n)

df = n − 1

Conditions:
→ σ unknown + any n  →  t-test (technically correct)
→ σ unknown + n < 30 →  t-test (must)

t-distribution:
→ Bell-shaped but fatter tails than normal
→ Fatter tails = more conservative (needs more extreme values to reject)
→ As df → large, t → normal distribution
```

**When:**
Small samples, unknown population SD — common in early-stage experiments, pilot studies, pilot products.

**Why:**
When we don't know σ and estimate it with s, we add uncertainty. Fatter t-distribution tails account for this extra uncertainty.

**General Example:**

```
New training program. n=12 employees, x̄=83, s=7, μ₀=75, α=0.05.
t = (83−75)/(7/√12) = 8/2.02 = 3.96
df=11. Critical t=1.796. 3.96 > 1.796 → Reject H₀.
Program significantly improves scores.
```

**Industry Example 1 — HR:**
15 employees tested after new onboarding. x̄=4.2 satisfaction, s=0.6, μ₀=3.8.
t=(4.2−3.8)/(0.6/√15)=2.58. df=14. Critical t=1.761. Reject H₀ → onboarding improved satisfaction.

**Industry Example 2 — Product:**
Pilot A/B test on 20 users. New feature: mean session duration x̄=7.5 min, s=2.1. Old: 6 min.
t=(7.5−6)/(2.1/√20)=3.19. Reject H₀ → new feature significantly increases engagement.

---

## 57. Z-Test vs T-Test

**What:**
Decision guide for choosing the correct test for comparing a mean to a hypothesized value.

**How:**

```
Z-Test:                          T-Test:
σ known         ✅               σ unknown → use s
n ≥ 30          ✅               n < 30 (especially)
Uses Z-table                     Uses t-table with df=n−1
Thinner tails                    Fatter tails
Z = (x̄−μ₀)/(σ/√n)             t = (x̄−μ₀)/(s/√n)

Decision flowchart:
σ known?
  YES → Z-test
  NO  → n ≥ 30? → Yes → Z or t (both fine, t preferred)
                → No  → t-test (must)
```

**When:**
Every time you test a mean. The choice of test matters for p-values and critical values.

**Why:**
Wrong test → wrong critical values → wrong conclusions → wrong business decisions.

**General Example:**
σ known = Z. σ unknown, n=10 = t. σ unknown, n=100 = both valid, t preferred.

**Industry Example 1 — Quality Audit:**
Machine output: σ known from process records → Z-test for efficiency.
New machine with no history → σ unknown, small pilot n=15 → t-test.

**Industry Example 2 — Clinical Trial:**
Phase I trial (n=20, σ unknown) → t-test.
Phase III trial (n=500, σ estimated) → Z-test acceptable (CLT), but t-test is still technically more appropriate.

---

## 58. One-Tailed vs Two-Tailed Test

**What:**
Determines where the rejection region sits — on one side or both sides of the distribution.

**How:**

```
Two-tailed (≠):
H₁: μ ≠ μ₀
α split: α/2 on each tail
Critical Z (α=0.05): ±1.96
Reject if Z < −1.96 OR Z > +1.96

Right-tailed (>):
H₁: μ > μ₀
All α on right tail
Critical Z (α=0.05): +1.645
Reject if Z > +1.645

Left-tailed (<):
H₁: μ < μ₀
All α on left tail
Critical Z (α=0.05): −1.645
Reject if Z < −1.645
```

**When:**
Two-tailed: when direction is unknown or you want to detect change in either direction.
One-tailed: when direction is specified by theory or prior knowledge.

**Why:**
One-tailed is more powerful in one direction but blind to the opposite. Two-tailed is more conservative but detects changes either way.

**General Example:**
"Is the drug different from placebo?" → Two-tailed.
"Does the drug reduce blood pressure?" → Left-tailed.
"Does the drug increase recovery speed?" → Right-tailed.

**Industry Example 1 — Marketing:**
"Is Campaign B different from A?" → Two-tailed.
"Is Campaign B BETTER than A?" → Right-tailed (more powerful, used when direction matters).

**Industry Example 2 — Manufacturing:**
"Is machine producing different from spec?" → Two-tailed.
"Is machine UNDER-producing?" → Left-tailed. Focus only on under-delivery, not over.

---

## 59. Z-Test for Proportion

**What:**
Tests whether a population proportion equals a hypothesized value. Used for binary/categorical outcomes.

**How:**

```
Z = (p̂ − p₀) / √[p₀(1−p₀) / n]

p̂  = x/n  (sample proportion)
p₀  = hypothesized proportion
n   = sample size

Conditions: np₀ ≥ 5  AND  n(1−p₀) ≥ 5
```

**When:**
Testing proportions — pass rates, conversion rates, defect rates, survey proportions.

**Why:**
Standard Z-test is for means. When the variable is binary (yes/no), proportion Z-test is the correct method.

**General Example:**
Claim: 60% of students pass on first attempt.
Survey n=200, 108 pass. p̂=0.54.
Z=(0.54−0.60)/√(0.60×0.40/200)=−1.73.
Critical Z(two-tailed)=±1.96. |Z|<1.96 → Fail to Reject H₀.

**Industry Example 1 — E-commerce:**
Claim: 25% of users complete checkout. Sample n=500, 110 complete (p̂=0.22).
Z=(0.22−0.25)/√(0.25×0.75/500)=−1.55. p=0.12 > 0.05 → Fail to reject. Not enough evidence checkout rate has fallen.

**Industry Example 2 — HR:**
Company claims 80% offer acceptance rate. Last quarter: n=150 offers, 108 accepted (p̂=0.72).
Z=(0.72−0.80)/√(0.80×0.20/150)=−2.45. Reject H₀ → Acceptance rate significantly below 80% → Review compensation.

---

## 60. Two-Proportion Z-Test

**What:**
Tests whether two population proportions are significantly different from each other.

**How:**

```
Pooled proportion: p̂c = (x₁+x₂)/(n₁+n₂)
Standard Error:    SE = √[p̂c(1−p̂c)(1/n₁+1/n₂)]
Test statistic:    Z = (p̂₁−p̂₂) / SE

H₀: p₁ = p₂
H₁: p₁ ≠ p₂  OR  p₁ > p₂  OR  p₁ < p₂

Why pooled? Under H₀, we assume p₁=p₂ → combine both samples
            for the best estimate of the common proportion.
```

**When:**
A/B testing, clinical trial treatment vs. control, comparing conversion rates, comparing pass rates across groups.

**Why:**
Tells us whether an observed difference between two proportions is real or just random variation.

**General Example:**

```
Group A: n=300, 72 successes → p̂₁=0.24
Group B: n=400, 80 successes → p̂₂=0.20
p̂c = 152/700 = 0.217
SE = √[0.217×0.783×(1/300+1/400)] = 0.0315
Z = (0.24−0.20)/0.0315 = 1.27 < 1.96 → Fail to reject H₀
```

**Industry Example 1 — Digital Marketing (A/B Test):**
Variant A: 500 users, 45 conversions (9%).
Variant B: 500 users, 65 conversions (13%).
Z-test p=0.02 < 0.05 → Reject H₀ → Variant B significantly better → Ship it.

**Industry Example 2 — Clinical Trial:**
Vaccine group: n=500, 45 sick (9%). Placebo: n=500, 90 sick (18%).
Z=−4.16. Reject H₀ → Vaccine significantly reduces illness rate. Used for regulatory submission.

---

## 61. Chi-Square Test

**What:**
A non-parametric test for categorical data. Tests whether observed frequencies match expected frequencies (GoF) or whether two categorical variables are associated (Independence).

**How:**

```
Formula: χ² = Σ[(O−E)²/E]

O = Observed frequency
E = Expected frequency

Two types:
1. Goodness of Fit:      df = k−1
   E = n × p₀

2. Test of Independence: df = (r−1)(c−1)
   E = (Row Total × Column Total) / Grand Total

Decision: χ²calc > χ²critical → Reject H₀
H₀: No difference / No association
H₁: Difference / Association exists
```

**When:**
Categorical variables. Testing if distribution fits expectation. Testing association between two categorical features.

**Why:**
Z-test and t-test are for numerical data. Chi-square handles categorical data — covering a large portion of real-world business data.

**GoF Example:**

```
Dice rolled 60 times. Expected 10 per face.
χ² = Σ(O−E)²/E = 2.20
df=5. Critical χ²=11.07. 2.20 < 11.07 → Fail to Reject → Dice is fair.
```

**Independence Example:**

```
Gender vs. product preference (2×2 table):
             A    B
Male        30   20
Female      20   30
χ² = 4.0. df=1. Critical=3.841. 4.0 > 3.841 → Reject H₀ → Association exists.
```

**Industry Example 1 — Marketing:**
Chi-square test: Is campaign response (yes/no) associated with age group (18-25, 26-40, 41+)?
Reject H₀ → response varies by age → segment campaigns by age group.

**Industry Example 2 — Feature Selection (ML):**
For classification models with categorical features, chi-square test determines which categorical features are statistically associated with the categorical target. Low chi-square p-value = feature is informative = keep it.

---

## 62. ANOVA & F-Test

**What:**
Analysis of Variance — tests whether means of 3 or more groups are significantly different. Uses F-statistic.

**How:**

```
H₀: μ₁ = μ₂ = μ₃ = ... = μₖ  (all group means equal)
H₁: At least one group mean is different

F = MSB / MSW
  = Variance BETWEEN groups / Variance WITHIN groups

F >> 1 → Between-group variation dominates → Groups differ → Reject H₀
F ≈ 1  → Within-group noise dominates → No significant difference

Why not multiple t-tests?
3 groups → 3 t-tests → Type I error inflates to ~14%
ANOVA tests all groups simultaneously → Type I error stays at α=0.05
```

**When:**
Comparing 3+ groups. Drug vs. 3 treatments. Sales across 5 regions. Scores across 4 teaching methods.

**Why:**
The only correct way to compare 3+ group means without inflating error rates.

**General Example:**
3 fertilizers on crop yield:
Fertilizer A: 42kg, Fertilizer B: 47kg, Fertilizer C: 44kg.
ANOVA tests: Are these differences real or just random variation?

**Industry Example 1 — Marketing:**
Compare average conversion rates across 4 ad campaign types (Email, Social, Search, Display). ANOVA determines if campaigns genuinely differ. If H₀ rejected → post-hoc test (Tukey's HSD) identifies which campaigns differ.

**Industry Example 2 — Manufacturing:**
3 production lines making the same product. ANOVA tests if mean defect rates differ across lines. F significant → one line has a process problem → targeted maintenance.

---

## 63. Pareto Distribution

**What:**
A power-law probability distribution that embodies the 80-20 rule: 80% of effects come from 20% of causes.

**How:**

```
Properties:
→ Right-skewed (heavy right tail)
→ Scale-free (ratio holds at any scale)
→ Few items have extreme values
→ Most items have small values

Pareto Chart:
→ Descending bar chart + Cumulative % line
→ Identify categories causing 80% of effect
```

**When:**
Prioritization, root cause analysis, resource allocation, inventory management.

**Why:**
Not all problems are equal. Pareto analysis focuses resources on the 20% that generates 80% of impact.

**General Example:**
20% of customers → 80% of revenue. Focus retention efforts on that 20%.

**Industry Example 1 — Customer Support:**
20% of issue categories → 80% of tickets. Pareto chart identifies top 3 issue types causing most complaints. Fix those first. Support workload drops dramatically.

**Industry Example 2 — Inventory:**
Inventory management uses Pareto (ABC analysis): A-items (top 20% by value) = 80% of inventory value → tightest controls. B and C items = looser controls. Reduces working capital.

---

## 64. Power Law Distribution

**What:**
A distribution where a small number of items are extremely common and most items are extremely rare. Scale-free.

**How:**

```
P(x) ∝ x^(−α)  (power law exponent α)

Properties:
→ Extreme right skew
→ No meaningful average (or mean is dominated by extremes)
→ Scale-free: ratio holds at any measurement scale
→ "Outliers" are expected, not rare
```

**When:**
Analyzing natural monopolies, network effects, social phenomena, wealth distribution.

**Why:**
Normal distribution assumes outliers are rare. Power law expects them. Using normal statistics on power law data gives completely wrong conclusions.

**General Example:**
Social media followers: most accounts have <1000 followers, a few have millions. This is power law, not normal.

**Industry Example 1 — Digital Media:**
Website traffic follows power law: top 1% of websites get ~50% of all internet traffic. A startup cannot benchmark against normal distribution — it needs power law thinking to understand the winner-takes-most dynamics.

**Industry Example 2 — VC / Startup:**
VC returns follow power law: 1-2 investments in a portfolio of 20 generate most of the returns. Portfolio construction strategy is built around this — diversify knowing power law will determine outcome.

---

## 65. Log-Normal Distribution

**What:**
A distribution where the logarithm of the variable follows a normal distribution. The variable itself is always positive and right-skewed.

**How:**

```
If Y = log(X) ~ Normal(μ, σ²)
Then X ~ Log-Normal

Properties:
→ Always right-skewed
→ All values > 0
→ Mean > Median > Mode
→ Generated by multiplicative (not additive) processes

Key transformation:
log(X) → normally distributed → apply all normal methods
→ Back-transform: exp(result) → original scale
```

**When:**
When natural log of your data is bell-shaped. Income, prices, biological measurements, loan amounts.

**Why:**
Applying normal-distribution methods to log-normal data gives wrong results. Log transformation is the fix.

**General Example:**
Salary data is log-normal: log(salary) is normally distributed. Analysis on log scale → transform back for reporting.

**Industry Example 1 — Finance:**
Stock prices follow log-normal distribution (can't go below zero, can theoretically go very high). Black-Scholes options pricing model assumes log-normal stock price distribution.

**Industry Example 2 — Healthcare:**
Bacterial colony sizes follow log-normal distribution. Drug dosages calculated after log transformation of concentration data to normalize it for statistical testing.

---

## 66. Box-Cox Transformation

**What:**
A family of power transformations that converts skewed data to approximately normal distribution, enabling use of normal-based statistical methods.

**How:**

```
y(λ) = (Xλ − 1) / λ    if λ ≠ 0
y(λ) = log(X)           if λ = 0

Common λ values:
λ = 1   → No change
λ = 0   → Log transformation
λ = 0.5 → Square root
λ = −1  → Inverse (1/X)
λ = 2   → Square

Process:
1. Check skewness
2. Apply Box-Cox → algorithm finds optimal λ
3. Verify transformed data ≈ normal
4. Build model on transformed data
5. Back-transform predictions
```

**When:**
Skewed target variables in regression, when ML models assume normality, when residuals are skewed.

**Why:**
Many statistical tests and ML models assume normality. Box-Cox converts skewed data to satisfy this assumption.

**General Example:**
Income data is right-skewed. Box-Cox with λ=0 (log transform) makes it approximately normal. Regression model now works properly.

**Industry Example 1 — Real Estate Pricing:**
House prices are right-skewed (few luxury properties). Box-Cox transform applied to price before regression modeling. RMSE improves significantly. Predictions back-transformed for client presentation.

**Industry Example 2 — Insurance:**
Claim amounts are heavily right-skewed. Box-Cox normalizes them. Linear regression on transformed claims → more accurate reserve estimation → better financial planning.

> ⚠️ Box-Cox requires all values > 0. For data with zeros or negatives → use Yeo-Johnson transformation.

---

## 67. Missing Values & Mean Imputation

**What:**
Missing values are data points absent from a dataset. Imputation replaces them with estimated values.

**How:**

**Types of Missing Data:**

```
MCAR: Missing Completely At Random → no pattern → can safely drop rows
MAR:  Missing At Random → depends on other observed variables → impute carefully
MNAR: Missing Not At Random → depends on the missing value → hardest to handle
```

**Disadvantages of Mean Imputation:**

```
1. Reduces variance artificially
   → All imputed values = mean → reduces spread
   → SD decreases → misleading statistics

2. Distorts distribution
   → Creates spike at the mean
   → Makes skewed data look more normal than it is

3. Breaks inter-variable correlations
   → Imputed values don't carry real information
   → Correlation between features gets diluted

4. Hides MNAR patterns
   → Missingness itself may be informative
   → Mean imputation erases this signal
```

**Better Alternatives:**

| Method                        | When to Use                       |
| ----------------------------- | --------------------------------- |
| **Median**              | Skewed data, outliers present     |
| **Mode**                | Categorical variables             |
| **KNN**                 | When feature relationships exist  |
| **Regression**          | When missingness can be predicted |
| **Multiple imputation** | When accuracy is critical         |
| **Drop**                | >50% missing in column            |

**When:**
Data cleaning phase, before EDA, before model training.

**Why:**
Missing values cause errors in calculations and biased model training. Treatment strategy depends on why values are missing.

**General Example:**
Age column has 5% missing values. Skewed age distribution → use median (not mean) imputation.

**Industry Example 1 — Credit Scoring:**
Income field has 8% missing values (higher-income customers less likely to disclose = MNAR). KNN imputation using occupation, location, loan amount as predictors. Simple mean imputation would underestimate income for this group.

**Industry Example 2 — Healthcare:**
Patient blood pressure missing for elderly patients (who missed follow-ups = MNAR). Multiple imputation using age, weight, medication as predictors. Mean imputation would ignore the systematic reason for missingness.

---

## 68. Outlier Detection Methods

**What:**
Methods to identify data points that deviate significantly from the rest of the dataset.

**How:**

### Method 1 — IQR Method (Robust)

```
IQR = Q3 − Q1
Lower fence = Q1 − 1.5 × IQR
Upper fence = Q3 + 1.5 × IQR

Below lower → outlier
Above upper → outlier

Robust: IQR itself is not affected by outliers
Best for: Skewed data, default choice
```

### Method 2 — Box Plot (Visual)

```
Points beyond whiskers = outliers
Whiskers extend to last value within fence
Dots plotted individually = confirmed outliers

Best for: Visual EDA, comparing groups side by side
```

### Method 3 — Z-Score Method

```
Z = (x − μ) / σ

|Z| > 3 → outlier (strong threshold)
|Z| > 2 → potential outlier (sensitive threshold)

NOT robust: mean and SD themselves get pulled by outliers
Best for: Approximately normally distributed data only
```

**Comparison:**

| Method   | Based on     | Robust? | Best for              |
| -------- | ------------ | ------- | --------------------- |
| IQR      | Quartiles    | ✅ Yes  | Skewed data, default  |
| Box Plot | IQR (visual) | ✅ Yes  | EDA, group comparison |
| Z-Score  | Mean & SD    | ❌ No   | Normal data only      |

**When:**
During EDA, before model training, during data validation pipelines.

**Why:**
Outliers distort mean, variance, correlation, and model training. Some outliers are data errors (remove). Some are real signals (investigate). Context determines treatment.

**General Example:**
Test scores: 60, 65, 70, 72, 95. IQR method → 95 is an outlier. Z-score: (95−72.4)/12.8=1.76 → not flagged by Z-score. IQR catches it, Z-score doesn't — shows why IQR is more reliable for small samples.

**Industry Example 1 — Finance:**
Daily transaction amounts: IQR method flags a ₹12L transaction as an outlier (upper fence = ₹3.5L). This is NOT removed — it's a high-value customer. Flagged for manual review. Outlier = signal, not error.

**Industry Example 2 — ML Feature Engineering:**
House prices before model training: Z-score fails because of extreme luxury prices pulling the mean. IQR method correctly identifies and caps extreme values at upper fence. Improves regression model RMSE by 18%.

---

## 🎯 Complete Interview Q&A Reference

| Topic       | Question                    | Answer                                                                                                                           |
| ----------- | --------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Stats Types | Descriptive vs Inferential? | Descriptive summarizes existing data. Inferential draws conclusions about a population from a sample using probability.          |
| Mean        | When NOT to use mean?       | When data is skewed or has outliers — mean gets pulled. Use median instead.                                                     |
| Variance    | Why divide by (n−1)?       | Bessel's correction — sample deviations from sample mean are smaller than from true population mean. (n−1) corrects this bias. |
| CLT         | Why does CLT matter?        | Real data is rarely normal. CLT says sample means are normal for n≥30 regardless — enabling normal-based tests on messy data.  |
| Z vs T      | When Z-test vs t-test?      | Z: σ known or n≥30. T: σ unknown especially n<30. T has fatter tails for extra uncertainty from estimating σ.                |
| CI          | What does 95% CI mean?      | If sampled 100 times, ~95 intervals would contain true μ. NOT "95% probability μ is in this interval."                         |
| P-value     | What is p-value?            | Probability of seeing this result (or more extreme) if H₀ is true. p<α → reject H₀.                                          |
| H₀         | Why never "accept H₀"?     | Failing to reject means insufficient evidence to disprove it, not that it's true. Absence of evidence ≠ evidence of absence.    |
| Correlation | Pearson vs Spearman?        | Pearson: linear, normal, no outliers. Spearman: rank-based, robust, ordinal or skewed data.                                      |
| Chi-Square  | When to use chi-square?     | Categorical data. GoF: does sample fit expected distribution? Independence: are two cat. variables associated?                   |
| Outliers    | IQR vs Z-score?             | IQR is robust (quartiles not affected by outliers). Z-score assumes normality and is sensitive to extremes. Default: IQR.        |
| Imputation  | Why avoid mean imputation?  | Reduces variance, distorts distribution, breaks correlations, hides MNAR patterns.                                               |
| Box-Cox     | Purpose of Box-Cox?         | Converts skewed data to normal using optimal power transformation. Requires X > 0.                                               |
| ANOVA       | Why not multiple t-tests?   | Inflates Type I error (~14% for 3 groups). ANOVA controls it at α=0.05 for all groups simultaneously.                           |

---

## ⚡ Master Cheat Sheet

```
CENTRAL TENDENCY
─────────────────────────────────────────────────────────────
Mean:    μ = Σx/N  |  x̄ = Σx/n          [sensitive to outliers]
Median:  Middle value (sorted)             [robust to outliers]
Mode:    Most frequent value               [only option for nominal data]

DISPERSION
─────────────────────────────────────────────────────────────
Population Variance:  σ²= Σ(x−μ)²/N
Sample Variance:      s² = Σ(x−x̄)²/(n−1)   ← Bessel's correction
Population SD:        σ  = √σ²
Sample SD:            s  = √s²

PERCENTILES & QUARTILES
─────────────────────────────────────────────────────────────
Q1=P25  |  Q2=P50=Median  |  Q3=P75
IQR = Q3 − Q1
Outlier fences: Q1−1.5×IQR  and  Q3+1.5×IQR

NORMAL DISTRIBUTION
─────────────────────────────────────────────────────────────
N(μ, σ²): symmetric, Mean=Median=Mode, area=1
Empirical: μ±1σ=68%  |  μ±2σ=95%  |  μ±3σ=99.7%
Z-score:  Z = (x−μ)/σ  →  N(0,1) standard normal
CLT:      x̄ ~ N(μ, σ²/n) for n≥30  |  SE = σ/√n

PROBABILITY RULES
─────────────────────────────────────────────────────────────
Basic:          P(A) = favorable/total
Complement:     P(A') = 1 − P(A)
Addition (ME):  P(A∪B) = P(A) + P(B)
Addition (Gen): P(A∪B) = P(A) + P(B) − P(A∩B)
Multiply (Ind): P(A∩B) = P(A) × P(B)
Multiply (Dep): P(A∩B) = P(A) × P(B|A)
Conditional:    P(B|A) = P(A∩B) / P(A)

DISTRIBUTIONS
─────────────────────────────────────────────────────────────
Bernoulli: 1 trial, p success. Mean=p, Var=p(1−p)
Binomial:  P(X=k) = ⁿCₖ×pᵏ×(1−p)^(n−k). Mean=np, Var=np(1−p)
Normal:    Bell curve, symmetric, defined by μ and σ
Log-Normal: log(X)~Normal, right-skewed, positive
Pareto:    80-20 rule, right-skewed, few dominate
Power Law: P(x)∝x^(−α), scale-free, extreme skew

COUNT METHODS
─────────────────────────────────────────────────────────────
Permutation: ⁿPᵣ = n!/(n−r)!           [Order MATTERS]
Combination: ⁿCᵣ = n!/(r!(n−r)!)       [Order does NOT matter]

CORRELATION
─────────────────────────────────────────────────────────────
Pearson:  r = Cov(X,Y)/(σₓ×σᵧ)        → linear, normal
Spearman: rₛ = 1−6Σd²/n(n²−1)          → rank-based, robust
Range: −1 ≤ r ≤ +1
Multicollinearity: |r|>0.85 between features → drop one

HYPOTHESIS TESTING
─────────────────────────────────────────────────────────────
Steps: H₀&H₁ → α → test → statistic → p-value → decide
p < α → Reject H₀  |  p ≥ α → Fail to Reject  |  NEVER "Accept"

Z-TEST:  σ known or n≥30  →  Z = (x̄−μ₀)/(σ/√n)
T-TEST:  σ unknown        →  t = (x̄−μ₀)/(s/√n),  df=n−1
Proportion Z: Z = (p̂−p₀)/√[p₀(1−p₀)/n]
2-Prop Z: p̂c=(x₁+x₂)/(n₁+n₂), Z=(p̂₁−p̂₂)/SE

CRITICAL VALUES (α=0.05)
─────────────────────────────────────────────────────────────
Two-tailed:   ±1.960
Right-tailed: +1.645
Left-tailed:  −1.645

CONFIDENCE INTERVAL
─────────────────────────────────────────────────────────────
CI = x̄ ± Z*×(σ/√n)
90%→Z*=1.645  |  95%→Z*=1.960  |  99%→Z*=2.576

CHI-SQUARE
─────────────────────────────────────────────────────────────
χ² = Σ[(O−E)²/E]
GoF: df=k−1  |  Independence: df=(r−1)(c−1)

ANOVA
─────────────────────────────────────────────────────────────
F = MSB/MSW  |  F>>1 → Reject H₀  |  3+ groups

OUTLIER DETECTION
─────────────────────────────────────────────────────────────
IQR (default): Q1−1.5×IQR  to  Q3+1.5×IQR
Z-score (normal data only): |Z|>3
```

---

## 🔗 Connect

- 🐙 GitHub: [@mmtiwari222](https://github.com/mmtiwari222)
- 💼 LinkedIn: Learning in public | AI-Powered Data Analyst
- 📓 Day-wise notes → Notion

---

*Complete 7-day Statistics for Data Analysis notes. Part of my DA → DS → ML → AI learning journey.*
*Nothing skipped. Everything covered. One concept at a time. 🚀*
