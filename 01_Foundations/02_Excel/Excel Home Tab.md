# 📊 Excel Home Tab — Complete Shortcut Keys & Notes

> **Madanmohan Tiwari** | IT Analyst → AI-Powered Data Analyst  
> Sindhuja Microcredit, Gurugram | June 2026

A complete, interview-ready reference for all **7 groups** of the Microsoft Excel Home Tab — shortcuts, concepts, real-world use cases, and interview Q&A.

---

## 📋 Table of Contents

- [What is the Home Tab?](#-what-is-the-home-tab)
- [Group 1 — Clipboard](#group-1--clipboard)
- [Group 2 — Font](#group-2--font)
- [Group 3 — Alignment](#group-3--alignment)
- [Group 4 — Number Format](#group-4--number-format)
- [Group 5 — Styles](#group-5--styles)
- [Group 6 — Cells](#group-6--cells)
- [Group 7 — Filtering · Tables · Slicers](#group-7--filtering--tables--slicers)
- [Interview Q&A](#-interview-qa)
- [Quick Reference Card](#-quick-reference-card)

---

## 💡 What is the Home Tab?

The **Home Tab** is the first and most-used tab in Microsoft Excel. It contains **7 groups** covering the most common spreadsheet operations — formatting, editing, data organization, and filtering.

> As a Data Analyst, **80% of daily Excel work** happens inside this one tab.

---

## Group 1 — Clipboard

Handles copying, cutting, and pasting data between cells, sheets, and workbooks.

| Shortcut | Action | Notes |
|---|---|---|
| `Ctrl + C` | Copy | Dashed border appears around selection |
| `Ctrl + X` | Cut | Original cell becomes empty after paste |
| `Ctrl + V` | Paste | Pastes values + formatting + formulas |
| `Ctrl + Alt + V` | Paste Special | Opens dialog — Values / Formats / Transpose |
| `Ctrl + Z` | Undo | Reverses last action |
| `Ctrl + Y` | Redo | Repeats undone action |
| `Alt + H + F + P` | Format Painter | Copies formatting to another cell or range |

### Paste Special Options (`Ctrl + Alt + V`)

| Option | Use Case |
|---|---|
| Values only | Remove formulas, keep numbers — use for final reports |
| Transpose | Flip rows ↔ columns |
| Formats only | Apply styling without copying data |
| Column widths | Paste only column width settings |

> 💡 **Real-world tip:** Copy disbursement data and **Paste as Values** into report sheets so formulas don't break when source data changes.

---

## Group 2 — Font

Controls the visual appearance of text inside cells.

| Shortcut | Action |
|---|---|
| `Ctrl + B` | Bold |
| `Ctrl + I` | Italic |
| `Ctrl + U` | Underline |
| `Ctrl + 5` | Strikethrough |
| `Alt + H + H` | Fill / background color |
| `Alt + H + FC` | Font color picker |
| `Alt + H + FF` | Change font face |
| `Alt + H + FS` | Change font size |
| `Alt + H + FG` | Increase font size |
| `Alt + H + FK` | Decrease font size |

### Tips

- Default font: **Calibri 11pt** — switch to Arial for professional reports
- Sizes: **10–12pt** for data cells, **14–16pt** for headers
- Color convention: 🔴 Red = errors &nbsp; 🟢 Green = success &nbsp; 🟡 Yellow = pending

> 💡 **Quick header formatting:** Select row → `Ctrl + B` → `Alt + H + H` (background) → `Alt + H + FC` (white font)

---

## Group 3 — Alignment

Controls how content is positioned inside a cell — horizontal, vertical, wrapping, indentation.

| Shortcut | Action |
|---|---|
| `Alt + H + AL` | Align Left |
| `Alt + H + AC` | Align Center |
| `Alt + H + AR` | Align Right |
| `Alt + H + AT` | Align Top |
| `Alt + H + AM` | Align Middle (vertical) |
| `Alt + H + AB` | Align Bottom |
| `Alt + H + W` | Wrap Text |
| `Alt + H + M + C` | Merge and Center |
| `Alt + H + M + U` | Unmerge Cells |
| `Alt + H + 6` | Increase Indent |
| `Alt + H + 9` | Decrease Indent |

### Key Concepts

- **Wrap Text** — forces long text to multiple lines inside a cell. Essential for description/comment columns.
- **Merge and Center** — use only for report titles. ⚠️ Avoid in data tables.
- **Center Across Selection** *(better alternative)* — looks identical to Merge but keeps cells independent.
  ```
  Ctrl + 1 → Alignment tab → Horizontal → Center Across Selection
  ```

> ⚠️ **Interview trap:** Merged cells break sorting, filtering, and VLOOKUP. Always use **Center Across Selection** in data tables instead of Merge and Center.

---

## Group 4 — Number Format

Controls how numeric values are **displayed**. The underlying value does not change — only the format.

| Shortcut | Action |
|---|---|
| `Ctrl + 1` | Format Cells dialog — full control |
| `Ctrl + Shift + $` | Currency format |
| `Ctrl + Shift + %` | Percentage format |
| `Ctrl + Shift + !` | Number with comma separator + 2 decimals |
| `Ctrl + Shift + #` | Date format (DD-MMM-YY) |
| `Ctrl + Shift + @` | Time format (HH:MM AM/PM) |
| `Ctrl + Shift + ^` | Scientific notation |
| `Alt + H + 0` | Increase decimal places |
| `Alt + H + 9` | Decrease decimal places |

### Format Types

| Format | Description |
|---|---|
| General | Default — Excel auto-decides |
| Number | Fixed decimals + optional comma separator |
| Currency | ₹/$ placed next to the value |
| Accounting | Symbol left-aligned, negatives in brackets — use for finance reports |
| Date | Serial number displayed as readable date |
| Percentage | `0.85` displayed as `85%` |
| Custom | `[Red]-#,##0;[Green]+#,##0` — negatives in red, positives in green |

> 💡 **Real-world use:**  
> Loan amounts → `Ctrl + Shift + $` &nbsp;|&nbsp; Repayment rate → `Ctrl + Shift + %`  
> Disbursement date → `Ctrl + Shift + #` &nbsp;|&nbsp; EMI with comma → `Ctrl + Shift + !`

---

## Group 5 — Styles

Applies pre-built and conditional formatting to make data visually meaningful at a glance.

| Shortcut | Action |
|---|---|
| `Alt + H + L` | Conditional Formatting menu |
| `Alt + H + T` | Format as Table |
| `Alt + H + S` | Cell Styles gallery |
| `Alt + H + H` | Fill / background color |
| `Alt + H + B` | Borders menu |

### Conditional Formatting Rule Types

| Rule | Example |
|---|---|
| Highlight Cell Rules | Values > 50,000 → highlight green |
| Top/Bottom Rules | Top 10 highest loan amounts |
| Data Bars | In-cell bars showing relative size |
| Color Scales | Red → Yellow → Green heat map |
| Icon Sets | Traffic lights / arrows / star ratings |

### Custom Formula Rule

```
1. Select range A2:D100
2. Alt + H + L → New Rule → "Use a formula to determine which cells to format"
3. Formula: =$C2>10000
→ Highlights the entire row where loan amount > ₹10,000
```

### Format as Table (`Ctrl + T`)

Converts a plain range into a structured Excel Table:

| Feature | Benefit |
|---|---|
| Auto-expand | New rows/columns join the table automatically |
| Structured references | `=Table1[Loan Amount]` instead of `=B2:B500` |
| Built-in total row | `Ctrl + Shift + T` to toggle |
| Auto filter | Headers get filter dropdowns automatically |
| Named range | Table name usable in formulas and PivotTables |

---

## Group 6 — Cells

Handles inserting, deleting, and resizing rows, columns, and sheets.

| Shortcut | Action |
|---|---|
| `Ctrl + Shift + +` | Insert cells / rows / columns |
| `Ctrl + -` | Delete cells / rows / columns |
| `Alt + H + I + R` | Insert row above selection |
| `Alt + H + I + C` | Insert column to the left |
| `Alt + H + D + R` | Delete selected row |
| `Alt + H + D + C` | Delete selected column |
| `Alt + H + O + I` | AutoFit column width ⭐ |
| `Alt + H + O + A` | AutoFit row height |
| `Alt + H + O + R` | Set row height manually |
| `Alt + H + O + W` | Set column width manually |
| `Alt + H + O + H` | Hide rows |
| `Alt + H + O + U` | Unhide rows |
| `Alt + H + V + S` | Insert new sheet |
| `Alt + H + D + S` | Delete sheet |
| `Alt + H + O + T` | Rename sheet |

### Key Concepts

- **AutoFit** (`Alt + H + O + I`) — permanently fixes the `######` display error
- **Hidden rows** still exist and are included in all formula calculations
- Inserting a row shifts all rows below downward — watch for hardcoded formula references

> 💡 **Delete all blank rows fast:**
> ```
> Ctrl + G → Special → Blanks → OK → Right-click → Delete → Entire Row
> ```

---

## Group 7 — Filtering · Tables · Slicers

The **most important group for Data Analysts.** Filter, sort, organize, and explore data interactively — no formulas needed.

| Shortcut | Action |
|---|---|
| `Ctrl + Shift + L` | Toggle AutoFilter on/off |
| `Alt + ↓` | Open filter dropdown for active column |
| `Alt + A + C` | Clear all active filters |
| `Ctrl + T` | Create a Table |
| `Ctrl + Shift + T` | Toggle Totals row in table |
| `Tab` (inside table) | Move right; creates new row at last column |
| `Alt + H + S + F` | Sort A to Z |
| `Alt + H + S + O` | Sort Z to A |
| `Alt + H + S + U` | Custom / multi-level sort dialog |
| `Ctrl + Shift + *` | Select current data region |
| `Alt + JT + SF` | Insert Slicer (Table must be selected) |
| `Ctrl + F3` | Name Manager |
| `Alt + F1` | Insert chart from selected data |

### AutoFilter — Step by Step

```
1. Click anywhere inside your dataset
2. Ctrl + Shift + L   →  dropdown arrows appear on all headers
3. Click a dropdown   →  choose filter value or condition
4. Alt + A + C        →  clear all filters and reset the view
```

**Filter condition examples:**

| Type | Example |
|---|---|
| Number | Greater than 50,000 |
| Text | Contains "Gurugram" |
| Date | This month / Last quarter |
| Color | Only red-highlighted rows |

### Excel Table vs Normal Range

| Feature | Normal Range | Excel Table |
|---|---|---|
| Auto-expand on new data | ❌ | ✅ |
| Structured references | ❌ | ✅ `Table1[Column]` |
| Built-in total row | ❌ Manual | ✅ `Ctrl + Shift + T` |
| Auto filter dropdowns | ❌ Manual | ✅ Automatic |
| Named range | ❌ | ✅ e.g. `Table1` |
| PivotTable / Slicer integration | Basic | Seamless |

### Multi-Level Sorting

```
Alt + H + S + U  →  Custom Sort dialog opens
→ Add Level 1: Branch Name    (A to Z)
→ Add Level 2: Loan Amount    (Largest to Smallest)
→ Click OK
```

### Slicers — Interactive Filtering

Slicers are **visual filter buttons** connected to a Table or PivotTable. They make dashboards interactive without any formulas.

```
1. Click inside your Table
2. Table Design tab → Insert Slicer  (Alt + JT + SF)
3. Choose columns to filter by: Branch, Status, Month
4. Click any slicer button to filter data instantly
```

| | Filter Dropdown | Slicer |
|---|---|---|
| Visibility | Hidden inside header | Always visible on screen |
| Click-to-filter | ❌ Requires dropdown steps | ✅ One click |
| Control multiple tables | ❌ | ✅ via Report Connections |
| Best for | Quick analysis | Dashboards, presentations |

> 💡 **Real-world use:**
> - Filter loan data by Branch or Center ID → AutoFilter
> - Show total disbursed amount → Table Total row (`Ctrl + Shift + T`)
> - Build interactive dashboard → Branch + Month Slicers
> - Field report → Multi-level sort by Center ID, then Customer Name

---

## 🎯 Interview Q&A

**Q1. What is the difference between Cut + Paste and Copy + Paste?**

Cut **moves** the data — the original cell becomes empty after pasting.  
Copy **duplicates** the data — the original cell stays unchanged.

---

**Q2. What does Paste Special do? Name 3 uses.**

`Ctrl + Alt + V` opens Paste Special:
1. **Values only** — removes formulas, keeps numbers. Use for final reports.
2. **Transpose** — flips rows and columns.
3. **Formats only** — applies styling without copying data.

---

**Q3. Why should you avoid Merge and Center in data tables?**

Merged cells **break sorting, filtering, and VLOOKUP/INDEX-MATCH**.  
Use **Center Across Selection** instead — looks identical but all cells remain independent.

---

**Q4. What is the difference between an Excel Table and a normal data range?**

An Excel Table (`Ctrl + T`) auto-expands when new data is added, supports structured references like `Table1[Loan Amount]`, has a built-in toggle total row, automatic filter dropdowns, and integrates seamlessly with PivotTables and Slicers.

---

**Q5. What is Conditional Formatting? Give 2 examples.**

Conditional Formatting automatically applies visual formatting based on cell value rules:
1. Highlight all loan amounts above ₹50,000 in green
2. Color scale — red for low repayment rate, green for high

---

**Q6. How do you fix the `######` error in Excel?**

The column is too narrow to display the value.  
Fix: Double-click the column border, or press `Alt + H + O + I` to AutoFit.

---

**Q7. What is a Slicer and when would you use it?**

A Slicer is a visual interactive filter button connected to a Table or PivotTable.  
Use it in **dashboards** — managers and stakeholders can filter by clicking buttons without touching the raw data.

---

**Q8. How do you sort data by multiple columns?**

`Alt + H + S + U` opens the Custom Sort dialog.  
Add multiple levels — e.g., sort by Branch (A→Z) first, then by Loan Amount (Largest→Smallest).

---

## ⚡ Quick Reference Card

| Group | Best Shortcut | Action |
|---|---|---|
| Clipboard | `Ctrl + Alt + V` | Paste Special |
| Font | `Ctrl + B / I / U` | Bold / Italic / Underline |
| Alignment | `Alt + H + W` | Wrap Text |
| Number | `Ctrl + 1` | Format Cells dialog |
| Styles | `Alt + H + L` | Conditional Formatting |
| Cells | `Alt + H + O + I` | AutoFit column width |
| Filter / Table | `Ctrl + T` | Create Table |
| Filter / Table | `Ctrl + Shift + L` | Toggle AutoFilter |

---


---

## 🛠️ Tech Stack

![Excel](https://img.shields.io/badge/Microsoft_Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![Notion](https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white)

---

## 👤 About Me

**Madanmohan Tiwari**  
IT Analyst @ Sindhuja Microcredit, Gurugram  
Learning path: `Data Analyst` → `Data Science` → `ML` → `Gen AI` → `Agentic AI`

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/madanmohan-tiwari)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/mmtiwari222)

---

*Learning in public. Building in public. One shortcut at a time.* 🚀