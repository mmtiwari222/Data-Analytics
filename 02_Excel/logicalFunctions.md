# 🧠 Excel Logical Functions — Complete Notes & Reference

> Part of my Data Analyst prep sprint — Day 6 of the Excel learning track.
> Covers IF, Nested IF, IFS, AND, OR, NOT, IFERROR, IFNA — with BFSI/microfinance real-world examples from my work at Sindhuja Microcredit.

---

## 📑 Table of Contents

- [Why Logical Functions Matter](#why-logical-functions-matter)
- [1. IF](#1-if--the-basic-decision-function)
- [2. Nested IF](#2-nested-if--multiple-conditions)
- [3. IFS](#3-ifs--cleaner-multi-condition-logic-excel-2019)
- [4. AND / OR / NOT](#4-and--or--not--combining-conditions)
- [5. IFERROR & IFNA](#5-iferror--ifna--error-handling)
- [6. Combining Logical + Lookup Functions](#6-combining-logical--lookup-functions)
- [Interview Q&A](#interview-qa--logical-functions)
- [Quick Reference Card](#quick-reference-card)

---

## Why Logical Functions Matter

Logical functions evaluate a condition and return different outputs based on whether it's TRUE or FALSE. They power every decision-based column in a Data Analyst's sheet — approval status, risk flags, pass/fail checks, category buckets.

> 💡 **Interview tip:** Logical functions + Lookup functions together cover ~70% of all Excel interview formula questions for Data Analyst roles.

---

## 1. IF — The Basic Decision Function

```excel
=IF(logical_test, value_if_true, value_if_false)
```

```excel
=IF(B2>=50000, "Eligible", "Not Eligible")
```

**Real-world use (Sindhuja Microcredit):**

```excel
=IF(C2="Paid", "Closed", "Active")
```
Flags loan status based on repayment column.

> 💡 **Interview tip:** IF always needs exactly 3 arguments in strict form, but `value_if_false` can be omitted — Excel returns `FALSE` by default if the condition fails and no third argument is given.

---

## 2. Nested IF — Multiple Conditions

Chaining IFs to test more than one condition in sequence.

```excel
=IF(B2>=75000, "High Value", IF(B2>=25000, "Medium Value", "Low Value"))
```

**Real-world use:**

```excel
=IF(D2>90, "A - Excellent", IF(D2>75, "B - Good", IF(D2>50, "C - Average", "D - Poor")))
```
Buckets loan repayment scores into grades.

**Key rules:**
- Excel allows up to 64 nested IFs, but more than 3-4 becomes unreadable — use IFS instead.
- Always test conditions from **highest to lowest** (or lowest to highest) consistently — mixing order causes logic errors.

> 💡 **Interview tip:** *"What's wrong with deeply nested IFs?"* → Hard to read, hard to debug, and easy to introduce logic errors when conditions overlap. IFS or lookup tables are cleaner alternatives.

---

## 3. IFS — Cleaner Multi-Condition Logic (Excel 2019+)

Tests multiple conditions in order and returns the result for the first TRUE one — no nesting required.

```excel
=IFS(condition1, value1, condition2, value2, ..., TRUE, default_value)
```

```excel
=IFS(D2>90, "A", D2>75, "B", D2>50, "C", TRUE, "D")
```

> 💡 **Interview tip:** Always add `TRUE, "default"` as the last pair — without it, IFS returns `#N/A` if no condition matches, which is a common bug.

---

## 4. AND / OR / NOT — Combining Conditions

| Function | Logic |
|---|---|
| `AND(cond1, cond2, ...)` | TRUE only if ALL conditions are TRUE |
| `OR(cond1, cond2, ...)` | TRUE if ANY condition is TRUE |
| `NOT(condition)` | Reverses TRUE/FALSE |

**Real-world use (Sindhuja Microcredit):**

```excel
=IF(AND(B2>=50000, C2="Active", D2<30), "High Priority Follow-up", "Normal")
```
Flags loans that are high value, still active, AND overdue by less than 30 days for priority calling.

```excel
=IF(OR(C2="Defaulted", C2="NPA"), "Risk", "Safe")
```
Flags any loan in either risk category.

> 💡 **Interview tip:** AND/OR return only TRUE/FALSE by themselves — they must be wrapped inside IF to produce a custom text output. `=AND(B2>50000,C2="Active")` alone just shows TRUE or FALSE.

---

## 5. IFERROR & IFNA — Error Handling

```excel
=IFERROR(formula, value_if_error)
=IFNA(formula, value_if_na)
```

**Real-world use:**

```excel
=IFERROR(VLOOKUP(A2, LMS_Data!A:F, 4, FALSE), "Not Found in LMS")
```
Replaces ugly `#N/A` errors with a readable message in client-facing reports.

| Function | Catches |
|---|---|
| IFERROR | ALL error types (#N/A, #REF!, #VALUE!, #DIV/0!, etc.) |
| IFNA | ONLY #N/A — lets other errors (like #REF!) surface for debugging |

> 💡 **Interview tip:** IFNA is safer in production formulas because it doesn't silently hide real errors like a broken cell reference — only masks the expected "not found" case.

---

## 6. Combining Logical + Lookup Functions

The real interview-winning skill: nesting logical functions around lookups.

```excel
=IF(ISNA(VLOOKUP(A2, LMS_Data!A:A, 1, FALSE)), "New Customer", "Existing Customer")
```

```excel
=IFS(
  AND(B2>=100000, C2="Active"), "VIP",
  AND(B2>=50000, C2="Active"), "Priority",
  TRUE, "Standard"
)
```
Segments customers into tiers based on loan amount and status — exactly the kind of formula asked in case-study interview rounds.

---

## Interview Q&A — Logical Functions

**Q1. Difference between nested IF and IFS?**
Nested IF chains multiple IF statements inside each other (hard to read past 3-4 levels); IFS evaluates a flat list of condition-value pairs in order and stops at the first TRUE — cleaner and easier to maintain.

**Q2. What happens if no condition matches in IFS and there's no default?**
IFS returns `#N/A`. Always include `TRUE, "default"` as the final pair to avoid this.

**Q3. Difference between IFERROR and IFNA?**
IFERROR catches every error type; IFNA only catches `#N/A`, letting other genuine errors (like `#REF!`) remain visible for debugging — which is safer in production formulas.

**Q4. Can AND/OR be used directly as a cell formula without IF?**
`=AND(B2>50000, C2="Active")` alone just returns `TRUE` or `FALSE` as the direct cell value — wrapping with IF lets you return custom text instead.

**Q5. How do you flag a customer as "New" if they don't exist in a lookup table?**
`=IF(ISNA(VLOOKUP(A2, Table, 1, FALSE)), "New Customer", "Existing Customer")` — ISNA checks if the VLOOKUP itself failed to find a match.

**Q6. What's the max number of nested IFs allowed and is it recommended?**
Excel allows up to 64, but more than 3-4 nested levels is a red flag in interviews — IFS, lookup tables, or CHOOSE are cleaner alternatives.

---

## Quick Reference Card

| Function | Best Use Case |
|---|---|
| IF | Single condition, two outcomes |
| Nested IF | 2-3 conditions max — beyond that, switch to IFS |
| IFS | Multiple conditions, flat readable structure |
| AND / OR | Combining multiple TRUE/FALSE checks |
| IFERROR | Hiding all error types with a fallback message |
| IFNA | Hiding only #N/A, keeping other errors visible |

---

*Notes by Madanmohan Tiwari | IT Analyst → AI-Powered Data Analyst Journey*
*Sindhuja Microcredit, Gurugram | July 2026*
