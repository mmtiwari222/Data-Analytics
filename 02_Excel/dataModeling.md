# 🥇 Excel Data Modeling — Power Pivot, Relationships & Star Schema Basics

> Part of my Data Analyst prep sprint — Day 11 of the Excel learning track.
> Covers Power Pivot setup, Fact vs Dimension tables, Star Schema, relationships, and troubleshooting — with BFSI/microfinance real-world examples from my work at Sindhuja Microcredit.

---

## 📑 Table of Contents

- [Why Data Modeling Matters](#why-data-modeling-matters)
- [1. Enabling Power Pivot](#1-enabling-power-pivot)
- [2. Fact Tables vs Dimension Tables](#2-fact-tables-vs-dimension-tables)
- [3. Star Schema](#3-star-schema--the-standard-data-model-shape)
- [4. Creating Relationships](#4-creating-relationships-between-tables)
- [5. Building a PivotTable from Multiple Tables](#5-building-a-pivottable-from-multiple-related-tables)
- [6. Common Relationship Errors](#6-common-relationship-errors)
- [Interview Q&A](#interview-qa--data-modeling)
- [Quick Reference Card](#quick-reference-card)

---

## Why Data Modeling Matters

Up to now, every PivotTable/formula worked on **one flat table**. Real business data lives in **multiple related tables** (Loans, Branches, Collections, Loan Officers) — Data Modeling lets you connect them without merging everything into one giant sheet using VLOOKUP. This is the exact skill that separates "Excel user" from "data analyst," and is a direct bridge to Power BI (same engine, same concepts).

> 💡 **Interview tip:** Power Pivot's Data Model uses the **same relationship engine as Power BI** — learning it here is not wasted effort, it transfers 1:1.

---

## 1. Enabling Power Pivot

**File → Options → Add-ins → COM Add-ins → check "Microsoft Power Pivot for Excel."**

Once enabled, a **Power Pivot** tab appears in the ribbon, and any query can be loaded straight into the **Data Model** (Power Query → Close & Load To → Add to Data Model).

---

## 2. Fact Tables vs Dimension Tables

| Table Type | Contains | Example |
|---|---|---|
| Fact Table | Transactional/numeric data, changes constantly, usually the largest table | Loan_Transactions (Loan ID, Date, Amount, Type) |
| Dimension Table | Descriptive/lookup data, relatively static, smaller table | Branch_Master (Branch ID, Branch Name, Region) |

**Real-world use (Sindhuja Microcredit):** **Fact Table:** Daily loan transactions (thousands of rows). **Dimension Tables:** Branch Master, Loan Officer Master, Product Master (each just tens/hundreds of rows) — all connected by ID columns instead of repeating branch names in every transaction row.

---

## 3. Star Schema — The Standard Data Model Shape

A **Star Schema** places one central Fact Table surrounded by multiple Dimension Tables, each connected by a single relationship (like spokes of a star).

```
        Branch_Master
              |
Officer_Master — Loan_Transactions — Product_Master
              |
         Date_Table
```

**Why Star Schema (not one giant flat table):**
- Avoids repeating Branch Name/Region text in every single transaction row (smaller file size).
- Update Branch info once in Branch_Master — it reflects everywhere instantly.
- Matches exactly how Power BI and SQL data warehouses are structured — transferable skill.

> 💡 **Interview tip:** *"Why not just VLOOKUP everything into one flat table?"* → A flat table duplicates dimension data on every row (bloats file size, harder to maintain), and breaks the moment you need a many-to-many relationship (e.g. one loan officer working across multiple branches).

---

## 4. Creating Relationships Between Tables

**Power Pivot → Manage → Diagram View**, then drag a field from one table to the matching field in another.

Or: **Data → Relationships → New** → select the two tables and the matching key column.

```
Loan_Transactions[Branch_ID]  ———  Branch_Master[Branch_ID]
```

**Cardinality types:**

| Type | Meaning | Example |
|---|---|---|
| One-to-Many | One dimension row relates to many fact rows (most common) | One Branch → many Loan Transactions |
| Many-to-Many | Requires a bridge table in classic modeling (native support in newer Excel) | Loan Officers who work across multiple Branches |

> 💡 **Interview tip:** Relationships should always go from a Dimension table's unique key to the Fact table's matching column — the Dimension side must have unique values for the relationship to work correctly (one-to-many, not many-to-many, unless explicitly modeled).

---

## 5. Building a PivotTable from Multiple Related Tables

Once relationships exist, insert a PivotTable and check **"Add this data to the Data Model"** — the field list now shows **all connected tables**, and you can drag fields from different tables into the same PivotTable, with Excel automatically joining them behind the scenes.

**Real-world use (Sindhuja Microcredit):** Drag **Branch Name** (from Branch_Master) to Rows and **Sum of Amount** (from Loan_Transactions) to Values — no VLOOKUP needed to bring Branch Name into the transactions table first.

---

## 6. Common Relationship Errors

| Issue | Cause | Fix |
|---|---|---|
| PivotTable shows blank/wrong totals | Relationship missing or built on the wrong column | Check Diagram View — confirm the join column matches exactly (same data type, matching IDs) |
| "Relationship may be needed" prompt | Dragged fields from two unrelated tables into one PivotTable | Click Auto-Detect, or manually create the relationship in Diagram View |
| Duplicate values inflate totals | Relationship built on a non-unique key on the "one" side | Ensure the Dimension table's key column has no duplicates |

---

## Interview Q&A — Data Modeling

**Q1. What's the difference between a Fact table and a Dimension table?**
Fact tables hold transactional/numeric data and grow constantly (e.g. loan transactions); Dimension tables hold descriptive, relatively static lookup data (e.g. branch names, product types) and are much smaller.

**Q2. Why use a Star Schema instead of one large flat table?**
It avoids duplicating dimension data (branch name, region) on every transaction row, keeps the file smaller, allows updating dimension info in one place, and matches how Power BI/SQL warehouses are structured — directly transferable knowledge.

**Q3. How do you connect two tables in Power Pivot?**
Power Pivot → Manage → Diagram View, then drag the matching key field from one table onto the corresponding field in the other table (or use Data → Relationships → New).

**Q4. What causes a PivotTable to show inflated/incorrect totals after adding a relationship?**
Usually a duplicate key on the "one" side of the relationship (the Dimension table) — the join multiplies rows unexpectedly. Fix by ensuring the Dimension table's key column is unique.

**Q5. Why does Power Pivot skill transfer directly to Power BI?**
Both tools use the exact same underlying Data Model engine and relationship/DAX concepts — learning star schema and relationships in Excel is not wasted effort when moving to Power BI later.

---

## Quick Reference Card

| Task | Where to Go |
|---|---|
| Enable Power Pivot | File → Options → Add-ins → COM Add-ins |
| View/edit table relationships | Power Pivot → Manage → Diagram View |
| Create a relationship without Power Pivot tab | Data → Relationships → New |
| Use fields from multiple tables in one PivotTable | Check "Add this data to the Data Model" when creating the PivotTable |
| Fix inflated totals | Ensure Dimension table key column has no duplicates |

---

*Notes by Madanmohan Tiwari | IT Analyst → AI-Powered Data Analyst Journey*
*Sindhuja Microcredit, Gurugram | July 2026*
