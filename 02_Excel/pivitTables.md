# 📈 Excel PivotTables — Deep Dive (Grouping, Calculated Fields, % of Total)

> Part of my Data Analyst prep sprint — Day 8 of the Excel learning track.
> Covers PivotTable basics, Value Field Settings, Grouping (dates & numbers), Calculated Fields, multi-level hierarchies, and refresh mechanics — with BFSI/microfinance real-world examples from my work at Sindhuja Microcredit.

---

## 📑 Table of Contents

- [Why PivotTables Matter](#why-pivottables-matter)
- [1. Building a Basic PivotTable](#1-building-a-basic-pivottable)
- [2. Value Field Settings — Beyond SUM](#2-value-field-settings--beyond-sum)
- [3. Grouping — Dates, Numbers, and Text](#3-grouping--dates-numbers-and-text)
- [4. Calculated Fields](#4-calculated-fields--custom-formulas-inside-a-pivottable)
- [5. Multi-Level Row/Column Hierarchies](#5-multi-level-rowcolumn-hierarchies)
- [6. Refreshing & Updating Source Data](#6-refreshing--updating-source-data)
- [Interview Q&A](#interview-qa--pivottables)
- [Quick Reference Card](#quick-reference-card)

---

## Why PivotTables Matter

A PivotTable summarizes large datasets into a compact, drag-and-drop report — without writing a single formula. It's the fastest way to answer "how much / how many, broken down by X" questions, and the #1 tool interviewers expect a Data Analyst to demonstrate live.

> 💡 **Interview tip:** If asked to "analyze this dataset" in a live Excel round, starting with a PivotTable (instead of manual formulas) immediately signals data-analyst-level thinking.

---

## 1. Building a Basic PivotTable

**Insert → PivotTable → select range → New Worksheet.**

| Zone | Purpose |
|---|---|
| Filters | Page-level filter above the table (e.g. Year) |
| Rows | Categories going down (e.g. Branch, Loan Officer) |
| Columns | Categories going across (e.g. Month, Status) |
| Values | The numbers being summarized (e.g. Sum of Disbursement) |

**Real-world use (Sindhuja Microcredit):** Drag **Branch** to Rows, **Loan Status** to Columns, **Disbursement Amount** to Values → instantly get a branch × status disbursement matrix across 300+ branches.

---

## 2. Value Field Settings — Beyond SUM

Right-click any value → **Value Field Settings** to change the summary type.

| Summary Type | Use Case |
|---|---|
| Sum | Total disbursement, total collections |
| Count | Number of loans per branch |
| Average | Average loan ticket size |
| Max / Min | Largest/smallest loan in a branch |
| % of Grand Total | Each branch's share of total disbursement |
| % of Column Total | Each status's share within its own month |
| Running Total In | Cumulative disbursement over months |
| Difference From | Month-over-month change in disbursement |

**Real-world use:** **Show Values As → % of Grand Total** on disbursement instantly shows which branches contribute most to the overall book — no manual formula needed.

> 💡 **Interview tip:** *"How do you show each category's contribution as a percentage?"* → Value Field Settings → Show Values As → % of Grand Total (or % of Column/Row Total depending on the breakdown needed).

---

## 3. Grouping — Dates, Numbers, and Text

**Grouping dates:** Right-click a date field in Rows → **Group** → choose Months, Quarters, Years.

```
Group by: Months, Quarters → auto-creates a Jan, Feb, Mar... or Q1, Q2... breakdown
```

**Grouping numbers (bucketing):** Right-click a numeric field → **Group** → set Starting/Ending value and interval.

```
Loan Amount grouped in bins of 25,000 → 0-25k, 25k-50k, 50k-75k...
```

**Real-world use (Sindhuja Microcredit):** Group **Disbursement Date** by Month + Year to get a monthly disbursement trend table in 2 clicks — replaces a manual MONTH()/YEAR() helper column approach.

> 💡 **Interview tip:** Grouping numeric fields into bins (e.g. loan amount ranges) is a very common ask — it's how you'd build a loan ticket size distribution report without SUMIFS/COUNTIFS.

---

## 4. Calculated Fields — Custom Formulas Inside a PivotTable

**PivotTable Analyze → Fields, Items & Sets → Calculated Field.**

```excel
Collection Efficiency % = Amount Collected / Amount Due
```

**Real-world use:** Create a Calculated Field for **Recovery Rate** = SUM(Collected) / SUM(Disbursed) that recalculates automatically as the underlying PivotTable filters change (e.g. filtering to one branch updates the recovery rate live).

> 💡 **Interview tip:** Calculated Fields operate on the **sum of underlying data**, not row-by-row averages — a common gotcha. `AVERAGE(A/B)` per row is not the same as `SUM(A)/SUM(B)` across all rows; PivotTable Calculated Fields always do the latter.

---

## 5. Multi-Level Row/Column Hierarchies

Drag multiple fields into Rows to create nested groupings.

```
Rows: Branch → Loan Officer → Loan Status
```

This creates a drill-down hierarchy: expand a branch to see officers, expand an officer to see status breakdown.

**Report layout options:**

| Layout | Look |
|---|---|
| Compact Form (default) | Indented single column, space-saving |
| Outline Form | Each field in its own column, subtotals per group |
| Tabular Form | Flat table-like layout, easiest to copy into other reports |

> 💡 **Interview tip:** Tabular Form is usually preferred for exporting PivotTable data into another tool (Power BI, SQL) since it avoids merged/indented cells.

---

## 6. Refreshing & Updating Source Data

```
PivotTable Analyze → Refresh (or Ctrl+Alt+F5 to refresh all PivotTables in the workbook)
```

**Making the source range dynamic:** Convert source data to an **Excel Table** (Ctrl+T) before creating the PivotTable — new rows added to the table are automatically included on refresh, no manual range editing needed.

> 💡 **Interview tip:** *"Your PivotTable isn't showing new rows I added — why?"* → The source range wasn't a Table, so new data falls outside the original PivotTable range. Convert to Table first, or manually update Change Data Source.

---

## Interview Q&A — PivotTables

**Q1. What's the difference between "% of Grand Total" and "% of Column Total"?**
% of Grand Total shows each cell's share of the entire PivotTable's sum; % of Column Total shows its share only within its own column (e.g. within that month).

**Q2. How do Calculated Fields handle averages differently from a normal AVERAGE formula?**
Calculated Fields always compute SUM(numerator) / SUM(denominator) across all underlying rows — not a row-by-row average — which can produce different results than expected.

**Q3. Why doesn't a PivotTable update when new rows are added to the source data?**
Because the original range reference doesn't auto-expand. Fix: convert source data to an Excel Table (Ctrl+T) before building the PivotTable, so new rows are automatically included.

**Q4. How do you create a loan-amount distribution report (e.g. 0-25k, 25k-50k buckets) using a PivotTable?**
Drag Loan Amount to Rows, then right-click → Group, and set the bucket interval (e.g. 25000) — Excel auto-creates the range buckets.

**Q5. Compact vs Tabular layout — when would you use each?**
Compact Form is best for on-screen viewing (space-saving, indented); Tabular Form is best when exporting the PivotTable output into another system, since every field gets its own column without indentation.

**Q6. How do you show month-over-month change in a PivotTable without extra formulas?**
Value Field Settings → Show Values As → "Difference From" → select the previous period as the base field.

---

## Quick Reference Card

| Task | Where to Go |
|---|---|
| Change Sum to Average/Count | Value Field Settings → Summarize Values By |
| Show as % of Total | Value Field Settings → Show Values As |
| Group dates by Month/Quarter | Right-click date field → Group |
| Bucket numeric ranges | Right-click numeric field → Group |
| Add a custom formula field | Analyze → Fields, Items & Sets → Calculated Field |
| Auto-update on new data | Convert source to Table (Ctrl+T) before creating PivotTable |

---

*Notes by Madanmohan Tiwari | IT Analyst → AI-Powered Data Analyst Journey*
*Sindhuja Microcredit, Gurugram | July 2026*
