# 📊 Excel Lookup & Reference Functions — Complete Notes & Reference

> Part of my Data Analyst prep sprint — Day 5 of the Excel learning track.
> Covers VLOOKUP, HLOOKUP, INDEX, MATCH, INDEX-MATCH, XLOOKUP, CHOOSE, OFFSET, and INDIRECT — with BFSI/microfinance real-world examples from my work at Sindhuja Microcredit.

---

## 📑 Table of Contents

- [Why Lookup & Reference Functions Matter](#why-lookup--reference-functions-matter)
- [1. VLOOKUP](#1-vlookup--vertical-lookup)
- [2. HLOOKUP](#2-hlookup--horizontal-lookup)
- [3. INDEX](#3-index--return-a-value-by-position)
- [4. MATCH](#4-match--return-a-position)
- [5. INDEX-MATCH](#5-index-match--the-interview-favorite)
- [6. XLOOKUP](#6-xlookup--the-modern-replacement-excel-365)
- [7. CHOOSE](#7-choose--pick-from-a-list-by-position)
- [8. OFFSET](#8-offset--dynamic-range-reference)
- [9. INDIRECT](#9-indirect--convert-text-into-a-reference)
- [10. Common Errors & Fixes](#10-common-lookup-errors--fixes)
- [Interview Q&A](#interview-qa--lookup--reference)
- [Quick Reference Card](#quick-reference-card)

---

## Why Lookup & Reference Functions Matter

Lookup & Reference functions find and retrieve data from a table or range based on a matching condition. They're the single most-asked topic in Data Analyst interviews, and the backbone of every reconciliation, merge, or cross-sheet reporting task — e.g. matching Loan IDs across LOS, LMS, and HROne exports at Sindhuja Microcredit.

> 💡 **Interview tip:** If asked "which Excel function do you use daily?" — Lookup functions (VLOOKUP / INDEX-MATCH / XLOOKUP) is always the safest, most credible answer for a Data Analyst role.

---

## 1. VLOOKUP — Vertical Lookup

Searches for a value in the **first column** of a range and returns a value from a specified column in the same row.

```excel
=VLOOKUP(lookup_value, table_array, col_index_num, [range_lookup])
```

| Argument | Meaning |
|---|---|
| `lookup_value` | The value you're searching for (e.g. Loan ID) |
| `table_array` | The full range containing the lookup column and return column |
| `col_index_num` | Column number (counting from 1) inside `table_array` to return |
| `range_lookup` | `FALSE` = exact match (default for DA work), `TRUE` = approximate match |

**Real-world use (Sindhuja Microcredit):**

```excel
=VLOOKUP(A2, LMS_Data!A:F, 4, FALSE)
```
Pulls the **Loan Status** from the LMS export sheet by matching Loan ID in column A.

**Key limitations:**
- Can only look **left to right** — lookup column must be the leftmost column in `table_array`.
- Breaks if a column is inserted inside `table_array` (`col_index_num` shifts).
- Slower on large datasets compared to INDEX-MATCH.
- Always **hardcode `FALSE`** for exact match unless doing slab/range lookups (e.g. interest rate slabs).

> 💡 **Interview tip:** *"Why does VLOOKUP fail with #N/A?"* → Usually leading/trailing spaces, mismatched data types (text vs number), or the lookup value doesn't exist in the first column of `table_array`.

---

## 2. HLOOKUP — Horizontal Lookup

Same logic as VLOOKUP, but searches across the **first row** and returns a value from a specified row number.

```excel
=HLOOKUP(lookup_value, table_array, row_index_num, [range_lookup])
```

**Real-world use:** Useful when monthly data is laid out **column-wise** (Jan, Feb, Mar as headers) instead of row-wise — common in MIS report templates.

```excel
=HLOOKUP("Mar-26", B1:M10, 5, FALSE)
```

> 💡 **Interview tip:** HLOOKUP is rarely used in real BFSI datasets since most data is row-wise, but interviewers ask it to test if you understand the row/column distinction vs VLOOKUP.

---

## 3. INDEX — Return a Value by Position

Returns the value at a given row/column intersection inside a range. **INDEX itself doesn't search — it just returns a value by position.**

```excel
=INDEX(array, row_num, [column_num])
```

```excel
=INDEX(D2:D500, 10)        ' 10th value in column D2:D500
=INDEX(A2:F500, 5, 3)      ' value at row 5, column 3 of the range
```

> 💡 **Interview tip:** INDEX is like asking Excel "what's in seat number 5, row 3?" — no searching involved, purely positional retrieval. This is exactly why it's faster than VLOOKUP.

---

## 4. MATCH — Return a Position

Searches for a value and returns its **relative position** (not the value itself) within a range.

```excel
=MATCH(lookup_value, lookup_array, [match_type])
```

| match_type | Behavior |
|---|---|
| `0` | Exact match (most common for DA work) |
| `1` | Largest value ≤ lookup_value (array must be sorted ascending) |
| `-1` | Smallest value ≥ lookup_value (array must be sorted descending) |

```excel
=MATCH("LN10023", A2:A500, 0)   ' returns position e.g. 47
```

> 💡 **Interview tip:** MATCH answers "where is it?" while VLOOKUP/INDEX answer "what is it?" — combining them is the classic INDEX-MATCH pattern.

---

## 5. INDEX-MATCH — The Interview Favorite

Combines INDEX (retrieve by position) with MATCH (find the position) to overcome every VLOOKUP limitation.

```excel
=INDEX(return_range, MATCH(lookup_value, lookup_range, 0))
```

**Real-world use (Sindhuja Microcredit):**

```excel
=INDEX(LMS_Data!D:D, MATCH(A2, LMS_Data!A:A, 0))
```
Pulls **Loan Status** (column D) by matching Loan ID (column A) — works even if columns are rearranged later.

**Why INDEX-MATCH beats VLOOKUP:**

| Feature | VLOOKUP | INDEX-MATCH |
|---|---|---|
| Lookup direction | Left to right only | Any direction (left or right) |
| Column insert safety | Breaks (`col_index_num` shifts) | Safe (column references, not numbers) |
| Performance on large data | Slower | Faster |
| Two-way (row + column) lookup | Not natively | Yes — nest two MATCH functions |

**Two-way lookup (row + column):**

```excel
=INDEX(B2:M50, MATCH(A55, A2:A50, 0), MATCH(B54, B1:M1, 0))
```
Looks up a Branch (row) **and** a Month (column) simultaneously — e.g. finding disbursement amount for "Gurugram" branch in "Mar-26".

> 💡 **Interview tip:** This is the #1 asked Excel interview question for Data Analyst roles: *"VLOOKUP vs INDEX-MATCH — which do you prefer and why?"* Always answer INDEX-MATCH, citing left-lookup flexibility and column-insert safety.

---

## 6. XLOOKUP — The Modern Replacement (Excel 365)

A single function that replaces VLOOKUP, HLOOKUP, and INDEX-MATCH — with built-in error handling.

```excel
=XLOOKUP(lookup_value, lookup_array, return_array, [if_not_found], [match_mode], [search_mode])
```

```excel
=XLOOKUP(A2, LMS_Data!A:A, LMS_Data!D:D, "Not Found")
```

**Why XLOOKUP wins:**
- Looks up in **any direction** (left or right) — no column counting.
- Built-in `if_not_found` argument replaces the need for `IFERROR(VLOOKUP(...))`.
- Defaults to **exact match** (safer than VLOOKUP's approximate default).
- Can return an **entire row or column** as an array, not just one value.
- `search_mode = -1` searches **last to first** — useful for finding the most recent transaction.

> 💡 **Interview tip:** If asked "Do you know XLOOKUP?" always say yes and mention it replaces both VLOOKUP and INDEX-MATCH with cleaner syntax — but INDEX-MATCH is still asked more in interviews since not all companies have Excel 365 yet.

---

## 7. CHOOSE — Pick from a List by Position

Returns a value from a list based on an index number.

```excel
=CHOOSE(index_num, value1, value2, ...)
```

```excel
=CHOOSE(2, "Low Risk", "Medium Risk", "High Risk")   ' → "Medium Risk"
```

**Real-world use:** Used with MATCH to build a lookup without a helper table:

```excel
=CHOOSE(MATCH(B2, {"A","B","C"}, 0), "Approved", "Pending", "Rejected")
```

---

## 8. OFFSET — Dynamic Range Reference

Returns a reference to a range that is a given number of rows/columns away from a starting cell.

```excel
=OFFSET(reference, rows, cols, [height], [width])
```

```excel
=SUM(OFFSET(A1, 1, 0, 12, 1))   ' sums 12 cells starting one row below A1
```

**Real-world use (Sindhuja Microcredit):** Building a **rolling 3-month disbursement total** that auto-adjusts as new months are added — common in dashboards.

> 💡 **Interview tip:** OFFSET is *volatile* (recalculates on every sheet change) — can slow down large workbooks. Interviewers sometimes ask for a non-volatile alternative → INDEX (since INDEX can also return a range reference and isn't volatile).

---

## 9. INDIRECT — Convert Text into a Reference

Converts a text string into an actual cell reference.

```excel
=INDIRECT(ref_text, [a1])
```

```excel
=INDIRECT("LMS_Data!A1")
=SUM(INDIRECT("Jan!" & "B2:B100"))
```

**Real-world use:** Building a dashboard that pulls from a **different month's sheet** based on a dropdown selection (e.g. cell A1 = "Mar" → INDIRECT builds the reference "Mar!B2").

> 💡 **Interview tip:** Also volatile like OFFSET. Common use case to mention: dynamically switching source sheets via a dropdown without rewriting formulas.

---

## 10. Common Lookup Errors & Fixes

| Error | Cause | Fix |
|---|---|---|
| `#N/A` | Lookup value not found, or text/number mismatch | Wrap in `IFERROR`, check `TRIM`/`VALUE`, verify exact match `FALSE` |
| `#REF!` | Column inside `table_array` was deleted | Switch to INDEX-MATCH which doesn't break on column shifts |
| `#VALUE!` | Wrong argument type passed (e.g. text where number expected) | Check row_num/col_num arguments are numeric |
| Wrong / approximate result | `range_lookup` left blank (defaults to `TRUE`) | Always specify `FALSE` explicitly for exact match |

```excel
=IFERROR(VLOOKUP(A2, LMS_Data!A:F, 4, FALSE), "Not in LMS")
```

---

## Interview Q&A — Lookup & Reference

**Q1. VLOOKUP vs INDEX-MATCH — which is better and why?**
INDEX-MATCH is preferred: it looks up in any direction (not just left-to-right), doesn't break when columns are inserted/deleted, and performs faster on large datasets.

**Q2. Can VLOOKUP look to the left of the lookup column?**
No — VLOOKUP always searches the leftmost column of `table_array` and returns from columns to its right. INDEX-MATCH or XLOOKUP is needed for left-lookups.

**Q3. What is the difference between MATCH and VLOOKUP?**
MATCH returns the **position** of a value within a range; VLOOKUP returns the actual **value** from a specified column. INDEX-MATCH combines both.

**Q4. How do you perform a two-way (row + column) lookup?**
`=INDEX(data_range, MATCH(row_value, row_range, 0), MATCH(column_value, column_range, 0))` — nesting two MATCH functions inside INDEX.

**Q5. What does the 4th argument of VLOOKUP (range_lookup) control?**
`FALSE` forces an exact match; `TRUE` (or omitted) allows an approximate match, which requires the lookup column to be sorted ascending — commonly used for interest rate/EMI slab lookups.

**Q6. Why is OFFSET considered risky in large workbooks?**
It's a volatile function — it recalculates every time any cell in the workbook changes, which can slow down performance significantly on large files.

**Q7. What advantage does XLOOKUP have over VLOOKUP?**
Searches in any direction, defaults to exact match, has a built-in "not found" argument (no need for IFERROR), and can return arrays instead of single values.

**Q8. How do you fix a VLOOKUP returning #N/A when the value clearly exists?**
Check for extra spaces (use `TRIM`), mismatched data types (numbers stored as text — use `VALUE`), or hidden characters; also confirm `FALSE` is used for exact match.

---

## Quick Reference Card

| Function | Best Use Case |
|---|---|
| VLOOKUP | Simple left-to-right lookup, quick one-off reports |
| HLOOKUP | Data laid out with headers across a row (months, quarters) |
| INDEX-MATCH | Reliable production formulas, any-direction lookup |
| XLOOKUP | Excel 365 workbooks, cleanest modern syntax |
| CHOOSE | Small fixed list, mapping a code to a label |
| OFFSET | Dynamic/rolling ranges (use sparingly — volatile) |
| INDIRECT | Dropdown-driven sheet switching (volatile) |

---

*Notes by Madanmohan Tiwari | IT Analyst → AI-Powered Data Analyst Journey*
*Sindhuja Microcredit, Gurugram | July 2026*
