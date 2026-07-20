# ➕ Excel Conditional Aggregation — SUMIFS, COUNTIFS, AVERAGEIFS

> Part of my Data Analyst prep sprint — Day 7 of the Excel learning track.
> Covers SUMIF, SUMIFS, COUNTIF, COUNTIFS, AVERAGEIF, AVERAGEIFS, SUMPRODUCT — with BFSI/microfinance real-world examples from my work at Sindhuja Microcredit.

---

## 📑 Table of Contents

- [Why Conditional Aggregation Matters](#why-conditional-aggregation-matters)
- [1. SUMIF](#1-sumif--sum-with-one-condition)
- [2. SUMIFS](#2-sumifs--sum-with-multiple-conditions)
- [3. COUNTIF](#3-countif--count-with-one-condition)
- [4. COUNTIFS](#4-countifs--count-with-multiple-conditions)
- [5. AVERAGEIF / AVERAGEIFS](#5-averageif--averageifs--conditional-average)
- [6. Counting Duplicates & Uniques](#6-counting-duplicates--uniques-with-countif)
- [7. SUMIFS vs SUMPRODUCT vs PivotTable](#7-sumifs-vs-sumproduct-vs-pivottable)
- [Interview Q&A](#interview-qa--conditional-aggregation)
- [Quick Reference Card](#quick-reference-card)

---

## Why Conditional Aggregation Matters

Conditional aggregation functions summarize data (sum, count, average) based on one or more matching criteria — the formula-based alternative to PivotTables, used constantly in quick MIS summaries, branch-wise totals, and reconciliation checks.

> 💡 **Interview tip:** SUMIFS/COUNTIFS questions almost always appear alongside VLOOKUP/INDEX-MATCH in the same interview round — they test if you can build a full summary report from raw transactional data.

---

## 1. SUMIF — Sum with One Condition

```excel
=SUMIF(range, criteria, [sum_range])
```

```excel
=SUMIF(C2:C500, "Gurugram", D2:D500)
```

**Real-world use (Sindhuja Microcredit):** Total loan disbursement for a single branch.

> 💡 **Interview tip:** If `sum_range` is omitted, SUMIF sums the `range` itself — useful for `=SUMIF(A2:A500,">50000")` (sum all values above 50,000 in the same column).

---

## 2. SUMIFS — Sum with Multiple Conditions

```excel
=SUMIFS(sum_range, criteria_range1, criteria1, criteria_range2, criteria2, ...)
```

> ⚠️ Unlike SUMIF, `sum_range` comes **first** in SUMIFS — a common mixup in interviews.

```excel
=SUMIFS(D2:D500, C2:C500, "Gurugram", E2:E500, "Active", F2:F500, ">=1-Jan-2026")
```

**Real-world use:** Total disbursement for Gurugram branch, only Active loans, disbursed on/after Jan 2026 — a typical 3-criteria MIS filter.

**Criteria operators:**

| Criteria | Meaning |
|---|---|
| `"Gurugram"` | Exact text match |
| `">50000"` | Greater than 50,000 |
| `"<>Closed"` | Not equal to "Closed" |
| `"*Micro*"` | Wildcard — contains "Micro" anywhere |
| `">="&A1` | Dynamic criteria referencing a cell |

---

## 3. COUNTIF — Count with One Condition

```excel
=COUNTIF(range, criteria)
```

```excel
=COUNTIF(E2:E500, "NPA")
```
Counts total loans marked as NPA (Non-Performing Asset).

---

## 4. COUNTIFS — Count with Multiple Conditions

```excel
=COUNTIFS(criteria_range1, criteria1, criteria_range2, criteria2, ...)
```

```excel
=COUNTIFS(C2:C500, "Gurugram", E2:E500, "Active")
```
Counts active loans specifically in the Gurugram branch.

**Real-world use:**

```excel
=COUNTIFS(F2:F500, ">=1-Jan-2026", F2:F500, "<=31-Jan-2026")
```
Counts disbursements within a date range (two conditions on the same column — a common interview trick question).

---

## 5. AVERAGEIF / AVERAGEIFS — Conditional Average

```excel
=AVERAGEIF(range, criteria, [average_range])
=AVERAGEIFS(average_range, criteria_range1, criteria1, ...)
```

```excel
=AVERAGEIFS(D2:D500, C2:C500, "Gurugram", E2:E500, "Active")
```
Average loan amount for active loans in Gurugram — same argument order pattern as SUMIFS.

---

## 6. Counting Duplicates & Uniques with COUNTIF

```excel
=COUNTIF(A2:A500, A2)>1          ' flags if this Loan ID appears more than once
=SUMPRODUCT(1/COUNTIF(A2:A500, A2:A500))   ' counts unique values (classic array trick)
```

> 💡 **Interview tip:** *"How do you find duplicate entries without Conditional Formatting?"* → `COUNTIF(range, cell)>1` wrapped in a helper column, or highlight with Conditional Formatting using the same formula.

---

## 7. SUMIFS vs SUMPRODUCT vs PivotTable

| Tool | Best For |
|---|---|
| SUMIF(S) | Quick single-cell summary formulas, works well in dashboards with dynamic criteria cells |
| SUMPRODUCT | Complex multi-condition math (OR logic across columns, weighted sums) |
| PivotTable | Full multi-dimensional summary reports, drag-drop flexibility, best for exploration |

> 💡 **Interview tip:** SUMIFS conditions are always **AND** logic by default. For OR logic (e.g. Branch = "Gurugram" OR "Noida"), you need `SUMIFS(...,"Gurugram") + SUMIFS(...,"Noida")` or a SUMPRODUCT with an array.

---

## Interview Q&A — Conditional Aggregation

**Q1. Difference between SUMIF and SUMIFS argument order?**
SUMIF: `range, criteria, sum_range` (sum_range last, optional). SUMIFS: `sum_range, criteria_range1, criteria1, ...` (sum_range always first, and it's mandatory). This is a classic interview trap question.

**Q2. How do you apply OR logic across SUMIFS conditions?**
SUMIFS only supports AND logic natively. For OR logic on the same field, add multiple SUMIFS together: `=SUMIFS(D:D,C:C,"Gurugram")+SUMIFS(D:D,C:C,"Noida")`.

**Q3. How do you count records within a date range using COUNTIFS?**
Use two conditions on the same column: `=COUNTIFS(F:F,">="&start_date, F:F,"<="&end_date)`.

**Q4. What does the wildcard `*` do inside COUNTIF/SUMIF criteria?**
Matches any sequence of characters — `"*Micro*"` matches any text containing "Micro" anywhere in the cell.

**Q5. How would you find duplicate Loan IDs in a 10,000-row sheet?**
`=COUNTIF(A:A, A2)>1` in a helper column, or apply Conditional Formatting with the same formula to highlight duplicates directly.

**Q6. When would you use SUMIFS over a PivotTable?**
When the summary needs to sit inside a live dashboard cell with dynamic criteria (e.g. driven by a dropdown), since SUMIFS recalculates instantly without needing a manual PivotTable refresh.

---

## Quick Reference Card

| Function | Best Use Case |
|---|---|
| SUMIF | One condition, quick total |
| SUMIFS | Multiple AND conditions, dashboard-ready totals |
| COUNTIF(S) | Counting records matching one/many conditions |
| AVERAGEIF(S) | Conditional average, same pattern as SUMIFS |
| SUMPRODUCT | OR logic, weighted sums, complex array math |

---

*Notes by Madanmohan Tiwari | IT Analyst → AI-Powered Data Analyst Journey*
*Sindhuja Microcredit, Gurugram | July 2026*
