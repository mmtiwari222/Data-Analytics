# 🔄 Excel Power Query — Get & Transform (Merge, Append, Unpivot, Clean Data)

> Part of my Data Analyst prep sprint — Day 10 of the Excel learning track.
> Covers Get Data, Merge Queries, Append Queries, Unpivot, Group By, and loading options — with BFSI/microfinance real-world examples from my work at Sindhuja Microcredit.

---

## 📑 Table of Contents

- [Why Power Query Matters](#why-power-query-matters)
- [1. Getting Data In](#1-getting-data-in)
- [2. Core Cleaning Steps](#2-the-power-query-editor--core-cleaning-steps)
- [3. Merge Queries](#3-merge-queries--power-querys-vlookupjoin)
- [4. Append Queries](#4-append-queries--stacking-tables)
- [5. Unpivot](#5-unpivot--turning-wide-data-into-longtidy-data)
- [6. Group By](#6-group-by--power-querys-sumifspivottable)
- [7. Closing & Loading](#7-closing--loading)
- [Interview Q&A](#interview-qa--power-query)
- [Quick Reference Card](#quick-reference-card)

---

## Why Power Query Matters

Power Query is Excel's built-in ETL (Extract, Transform, Load) tool. Instead of manually cleaning a messy CSV every month, you build the cleaning steps **once** as a query — then just hit Refresh next month and the same steps re-run automatically on new data. This is the single biggest skill jump from "formula-based Excel" to "data-analyst-grade Excel."

> 💡 **Interview tip:** If asked "how do you handle messy/inconsistent source data every month," Power Query is the expected answer — not "I clean it manually each time."

---

## 1. Getting Data In

**Data → Get Data → From File / From Database / From Web / From Table-Range.**

| Source | Use Case |
|---|---|
| From Table/Range | Cleaning data already inside the current workbook |
| From Folder | Combining many files with the same structure (e.g. monthly branch exports) into one table |
| From CSV/Text | Loading raw exports from LOS/LMS systems |
| From Web | Pulling a table directly from a webpage |

**Real-world use (Sindhuja Microcredit):** **From Folder**: point Power Query at a folder containing 300+ branch-wise monthly Excel exports → it automatically combines all of them into a single clean table, applying the same transformation steps to each file.

---

## 2. The Power Query Editor — Core Cleaning Steps

Every action you take (remove column, rename, filter, split) becomes a recorded **Applied Step** — fully undoable and re-runnable on refresh.

| Transformation | Where |
|---|---|
| Remove/keep columns | Right-click column header → Remove / Remove Other Columns |
| Change data type | Click the data type icon in column header |
| Split a column | Transform → Split Column (by delimiter or by number of characters) |
| Trim/Clean text | Transform → Format → Trim / Clean |
| Filter rows | Click the filter dropdown on any column header |
| Remove duplicates | Home → Remove Rows → Remove Duplicates |
| Remove errors/blanks | Home → Remove Rows → Remove Errors / Remove Blank Rows |

**Real-world use:** A raw LOS export often has inconsistent Loan ID formatting (extra spaces, mixed case) — Trim + Clean + Uppercase/Lowercase transformation steps fix this once, and every future refresh applies the same fix automatically.

> 💡 **Interview tip:** *"How is Power Query different from just cleaning data manually?"* → Every step is recorded and replayable — clean once, refresh forever, versus repeating manual fixes every time new data arrives.

---

## 3. Merge Queries — Power Query's VLOOKUP/JOIN

**Home → Merge Queries** (or Merge Queries as New to keep the originals separate).

Combines two tables based on a matching column — exactly like a SQL JOIN.

| Join Type | Excel Equivalent / SQL Equivalent |
|---|---|
| Left Outer | All rows from Table 1 + matches from Table 2 (like VLOOKUP) |
| Right Outer | All rows from Table 2 + matches from Table 1 |
| Full Outer | All rows from both tables |
| Inner | Only rows that match in both tables |
| Left Anti | Only rows in Table 1 with NO match in Table 2 (find missing records) |

**Real-world use (Sindhuja Microcredit):** Merge the **Loan Master** table with the **Collections** table on Loan ID (Left Outer join) to bring Collection Amount next to every loan record — replaces a manual VLOOKUP column.

> 💡 **Interview tip:** *"How do you find records that exist in one table but not another?"* → Merge Queries with **Left Anti** join type — this is the Power Query equivalent of finding VLOOKUP #N/A rows, but done for the entire table at once.

---

## 4. Append Queries — Stacking Tables

**Home → Append Queries** (or Append Queries as New).

Stacks two or more tables with the **same columns** on top of each other — combining multiple months/branches into one long table.

**Real-world use:** Append 12 monthly disbursement sheets (Jan, Feb, Mar... Dec) into a single yearly table — the foundation needed before building any PivotTable or Data Model relationship.

> 💡 **Interview tip:** Merge = combining columns (VLOOKUP-style, side-by-side); Append = combining rows (stacking, UNION-style). This distinction is one of the most common Power Query interview questions.

---

## 5. Unpivot — Turning Wide Data into Long/Tidy Data

Most raw exports have months or categories spread **across columns** (wide format) — unusable for PivotTables or Power BI, which need **long/tidy format** (one row per observation).

**Select the columns to unpivot → Transform → Unpivot Columns.**

**Before (wide format):**
```
Branch | Jan | Feb | Mar
GGN    | 5L  | 6L  | 7L
```

**After (long/tidy format via Unpivot):**
```
Branch | Attribute | Value
GGN    | Jan       | 5L
GGN    | Feb       | 6L
GGN    | Mar       | 7L
```

**Real-world use (Sindhuja Microcredit):** MIS reports are often exported with months as separate columns — Unpivot instantly converts this into a Date + Value structure usable in a PivotTable or as a Power BI source.

> 💡 **Interview tip:** *"Why does a PivotTable/Power BI need data in long format instead of wide format?"* → Analytical tools group and aggregate by column values — wide format (months as columns) can't be grouped/filtered the same way a single "Month" column can.

---

## 6. Group By — Power Query's SUMIFS/PivotTable

**Transform → Group By** — aggregates rows by one or more columns, similar to a PivotTable but as a repeatable query step.

```
Group By: Branch → New Column: Total Disbursement = Sum of Amount
```

---

## 7. Closing & Loading

**Home → Close & Load** (loads to a new worksheet) or **Close & Load To...** (choose PivotTable Report, existing sheet, or Only Create Connection — useful for feeding a Data Model without duplicating data on a sheet).

> 💡 **Interview tip:** "Only Create Connection" + "Add to Data Model" is the correct choice when a query is only meant to feed a Power Pivot data model, not sit as a visible sheet — keeps the workbook lighter.

---

## Interview Q&A — Power Query

**Q1. What is the core benefit of Power Query over manual data cleaning?**
Every cleaning step is recorded as a reusable, refreshable query — clean the process once, and it re-applies automatically to new data on every refresh, instead of repeating manual fixes each time.

**Q2. Difference between Merge and Append?**
Merge combines tables side-by-side based on a matching column (like a SQL JOIN/VLOOKUP); Append stacks tables with the same columns on top of each other (like a SQL UNION).

**Q3. How do you find rows that exist in one table but not another using Power Query?**
Merge Queries using a **Left Anti** join — returns only the rows from the first table with no match in the second.

**Q4. Why would you Unpivot a table before building a PivotTable or feeding Power BI?**
Analytical tools need data in long/tidy format (one row per observation) to group, filter, and aggregate correctly; wide format (e.g. months as separate columns) can't be aggregated the same way.

**Q5. What does "Only Create Connection" do when loading a query?**
Loads the query's output into the workbook's Data Model (for use in Power Pivot/PivotTables) without creating a visible worksheet, keeping the file lighter.

**Q6. How would you combine 12 monthly Excel files with identical structure into one table automatically?**
Use Get Data → From Folder — Power Query combines all files in the folder using the same transformation steps, and picks up new files automatically on refresh.

---

## Quick Reference Card

| Task | Where to Go |
|---|---|
| Combine tables side-by-side (JOIN) | Home → Merge Queries |
| Stack tables on top of each other (UNION) | Home → Append Queries |
| Convert wide format to long/tidy format | Transform → Unpivot Columns |
| Aggregate rows by category | Transform → Group By |
| Combine many files automatically | Get Data → From Folder |
| Load only to Data Model (no sheet) | Close & Load To → Only Create Connection + Add to Data Model |

---

*Notes by Madanmohan Tiwari | IT Analyst → AI-Powered Data Analyst Journey*
*Sindhuja Microcredit, Gurugram | July 2026*
