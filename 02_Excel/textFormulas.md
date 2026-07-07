# 📝 Excel Text Formulas — Complete Reference

> **Madanmohan Tiwari** | IT Analyst → AI-Powered Data Analyst  
> Sindhuja Microcredit, Gurugram | June 2026

Complete reference for all Excel text formulas — with syntax, examples, real-world use cases, and interview Q&A.

---

## 📋 Table of Contents

- [Why text formulas matter](#-why-text-formulas-matter)
- [Category 1 — Case Conversion](#category-1--case-conversion)
- [Category 2 — Extract Text](#category-2--extract-text)
- [Category 3 — Length & Search](#category-3--length--search)
- [Category 4 — Clean & Trim](#category-4--clean--trim)
- [Category 5 — Join & Repeat](#category-5--join--repeat)
- [Category 6 — Convert & Format](#category-6--convert--format)
- [Power Combinations](#-power-combinations--real-world-formulas)
- [Interview Q&A](#-interview-qa)
- [Quick Reference Table](#-quick-reference-table)

---

## 💡 Why Text Formulas Matter

Real-world data is messy. Names have wrong cases, numbers are stored as text, cells have extra spaces, and system exports contain invisible characters. Text formulas are your **data cleaning toolkit** — before you can analyze data, you need to clean it.

---

## Category 1 — Case Conversion

### `UPPER(text)`
Converts all characters to UPPERCASE.

```excel
=UPPER("hello world")    → HELLO WORLD
=UPPER(A2)
```

> **Use case:** Standardize city or customer names before VLOOKUP comparisons.

---

### `LOWER(text)`
Converts all characters to lowercase.

```excel
=LOWER("HELLO WORLD")    → hello world
=LOWER(A2)
```

> **Use case:** Normalize email addresses before matching — always compare emails in lowercase.

---

### `PROPER(text)`
Capitalizes the first letter of every word, lowercases the rest.

```excel
=PROPER("john doe")      → John Doe
=PROPER("RAVI KUMAR")    → Ravi Kumar
=PROPER(TRIM(A2))        → fixes case AND removes extra spaces
```

> **Use case:** Fix customer name data imported from field apps where all-caps entries are common.

---

## Category 2 — Extract Text

### `LEFT(text, num_chars)`
Returns `num_chars` characters from the start (left) of a string.

```excel
=LEFT("Excel", 3)        → Exc
=LEFT(A2, 5)             → first 5 characters of cell A2
```

### `RIGHT(text, num_chars)`
Returns `num_chars` characters from the end (right) of a string.

```excel
=RIGHT("Excel", 3)       → cel
=RIGHT(A2, 6)            → last 6 characters
```

### `MID(text, start_num, num_chars)`
Returns `num_chars` characters starting at `start_num` position.

```excel
=MID("Excel", 2, 3)      → xce   (start at 2, take 3 chars)
=MID(A2, 5, 4)           → 4 characters starting from position 5
```

**Name splitting with LEFT + FIND + RIGHT:**
```excel
First name:  =LEFT(A2, FIND(" ", A2)-1)
Last name:   =RIGHT(A2, LEN(A2)-FIND(" ", A2))
```

> **Use case:** Extract branch code from a structured loan ID like `MFI-DEL-2024-001`.

---

## Category 3 — Length & Search

### `LEN(text)`
Returns the total number of characters including spaces.

```excel
=LEN("Hello")            → 5
=LEN("Hello World")      → 11
```

> **Use case:** Validate mobile numbers are exactly 10 digits — flag rows where `=LEN(A2)<>10`.

---

### `FIND(find_text, within_text, [start_num])`
Returns the **position** of a substring. **Case-sensitive. No wildcards.**

```excel
=FIND("e", "Excel")      → 4   (lowercase e only)
=FIND("@", A2)           → position of @ in email
=FIND(" ", A2)           → position of first space
=IFERROR(FIND("@",A2), "Not found")   ← wrap in IFERROR for safety
```

---

### `SEARCH(find_text, within_text, [start_num])`
Same as FIND but **case-insensitive** and supports **wildcards** (`*` and `?`).

```excel
=SEARCH("e", "Excel")    → 1   (finds E at position 1)
=SEARCH("ex*", A2)       → finds anything starting with 'ex'
=SEARCH("l??n", A2)      → finds 4-char pattern like 'loan'
```

| | `FIND` | `SEARCH` |
|---|---|---|
| Case-sensitive | ✅ Yes | ❌ No |
| Wildcards `* ?` | ❌ No | ✅ Yes |
| Returns | Position number | Position number |
| Error if not found | ✅ | ✅ |

---

### `EXACT(text1, text2)`
Compares two strings exactly — case-sensitive. Returns TRUE or FALSE.

```excel
=EXACT("Hello", "hello")     → FALSE
=EXACT("Hello", "Hello")     → TRUE
=EXACT(A2, B2)
```

> **Use case:** Validate that a code or ID was entered exactly right.

---

## Category 4 — Clean & Trim

### `TRIM(text)`
Removes leading/trailing spaces and reduces multiple internal spaces to one.

```excel
=TRIM("  Hello  World  ")    → Hello World
=TRIM(A2)
```

> ⚠️ **Critical:** Invisible extra spaces cause VLOOKUP and MATCH to silently fail. Always TRIM before lookups on imported data.

---

### `CLEAN(text)`
Removes non-printable characters (ASCII codes 0–31) — invisible characters from system imports.

```excel
=CLEAN(A2)
=TRIM(CLEAN(A2))             ← best practice: combine both
```

> **Use case:** Data from banking systems or LMS exports often contains hidden characters. CLEAN removes them.

---

### `SUBSTITUTE(text, old_text, new_text, [instance_num])`
Replaces a specific text value with new text. Optional 4th argument specifies which occurrence.

```excel
=SUBSTITUTE("a-b-c", "-", "/")        → a/b/c
=SUBSTITUTE("aaa", "a", "b", 2)       → aba   (replace only 2nd occurrence)
=SUBSTITUTE(A2, " ", "_")             → replaces all spaces with underscores
```

---

### `REPLACE(text, start_num, num_chars, new_text)`
Replaces characters at a **fixed position** — regardless of what the characters are.

```excel
=REPLACE("ABC123", 4, 3, "456")       → ABC456
=REPLACE(A2, 1, 3, "NEW")            → replaces first 3 chars with NEW
```

> **SUBSTITUTE vs REPLACE:**
> - SUBSTITUTE → replace by **value** (what the text says)
> - REPLACE → replace by **position** (where in the string)

---

## Category 5 — Join & Repeat

### `CONCATENATE(text1, text2, ...)` / `CONCAT()` / `&`

```excel
=CONCATENATE("Hello", " ", "World")    → Hello World
=CONCAT(A2, " ", B2)                   → same, newer syntax (Excel 2019+)
=A2 & " " & B2                         → simplest, works all versions
=A2 & ", " & B2 & ", " & C2            → chain multiple
```

> **Best practice:** Use `&` for simple joins, `TEXTJOIN` for ranges.

---

### `TEXTJOIN(delimiter, ignore_empty, text1, ...)`
Joins a range of cells with a delimiter. Skips blank cells if `ignore_empty` is TRUE.

```excel
=TEXTJOIN(", ", TRUE, A1:A5)           → a, b, c      (blanks skipped)
=TEXTJOIN(", ", FALSE, A1:A5)          → a, , b, , c  (blanks included)
=TEXTJOIN(" | ", TRUE, B2:B20)         → joins all names with pipe
```

> **Use case:** Create a comma-separated list of branch names or join multiple fields into one summary column.

---

### `REPT(text, number_times)`
Repeats a text string a specified number of times.

```excel
=REPT("*", 5)                          → *****
=REPT("█", A2/100)                     → in-cell visual bar chart
=REPT("-", LEN(A2))                    → separator line matching cell length
```

---

## Category 6 — Convert & Format

### `TEXT(value, format_text)`
Converts a number to a text string with a specific display format. Result is TEXT — cannot be used in math.

```excel
=TEXT(1234.5, "#,##0.00")              → 1,234.50
=TEXT(TODAY(), "DD-MMM-YYYY")          → 05-Jun-2026
=TEXT(0.856, "0%")                     → 86%
=TEXT(B2, "₹#,##0")                    → ₹50,000
="Loan amount: " & TEXT(B2,"₹#,##0")  → Loan amount: ₹50,000
```

> ⚠️ TEXT returns a string — you cannot SUM or do math on it afterwards.

---

### `VALUE(text)`
Converts a number stored as text back to a real number.

```excel
=VALUE("1234")                         → 1234
=VALUE("12.5%")                        → 0.125
=VALUE(TRIM(A2))                       → clean then convert
```

> **Use case:** Data from Krytrim LMS or bank exports often has amounts as text (left-aligned, green corner triangle). VALUE converts them so SUM works correctly.

---

### `CHAR(number)`
Returns the character for a given ASCII code number.

```excel
=CHAR(65)                              → A
=CHAR(97)                              → a
=CHAR(10)                              → line break
=A2 & CHAR(10) & B2                   → two lines in one cell (enable Wrap Text)
```

---

### `CODE(text)`
Returns the ASCII code for the first character of a text string. Reverse of CHAR.

```excel
=CODE("A")                             → 65
=CODE("a")                             → 97
=CODE(A2)                              → code of first character in A2
```

---

## ⚡ Power Combinations — Real-World Formulas

### Name handling
```excel
Extract first name:    =LEFT(A2, FIND(" ", A2)-1)
Extract last name:     =RIGHT(A2, LEN(A2)-FIND(" ", A2))
Full clean + fix case: =PROPER(TRIM(A2))
```

### Email parsing
```excel
Extract username:      =LEFT(A2, FIND("@",A2)-1)
Extract domain:        =MID(A2, FIND("@",A2)+1, LEN(A2))
Check contains @:      =ISNUMBER(SEARCH("@", A2))
```

### Data cleaning
```excel
Full clean pipeline:   =PROPER(TRIM(CLEAN(A2)))
Remove dashes:         =SUBSTITUTE(A2, "-", "")
Replace spaces:        =SUBSTITUTE(A2, " ", "_")
Validate phone length: =LEN(SUBSTITUTE(A2," ",""))=10
```

### Number ↔ text conversion
```excel
Number to label:       ="EMI: " & TEXT(B2, "₹#,##0")
Text to number:        =VALUE(TRIM(A2))
Date as text:          =TEXT(C2, "DD/MM/YYYY")
```

### String checks
```excel
Contains word:         =ISNUMBER(SEARCH("loan", A2))
Exact match:           =EXACT(A2, B2)
Starts with prefix:    =LEFT(A2, 3)="MFI"
Ends with suffix:      =RIGHT(A2, 3)="Ltd"
Nth character:         =MID(A2, 3, 1)="X"
```

---

## 🎯 Interview Q&A

**Q1. What is the difference between FIND and SEARCH?**

FIND is case-sensitive and does not support wildcards. SEARCH is case-insensitive and supports `*` (any characters) and `?` (single character). Both return a position number and error if not found.

---

**Q2. What does TRIM do and why is it important?**

TRIM removes leading/trailing spaces and reduces multiple spaces between words to one. It is critical because invisible spaces cause VLOOKUP and MATCH to silently fail — two cells that look identical may not match if one has a trailing space.

---

**Q3. What is the difference between SUBSTITUTE and REPLACE?**

SUBSTITUTE replaces by **value** — finds a specific text and replaces it. REPLACE replaces by **position** — always replaces characters at a fixed location regardless of what they are.

---

**Q4. Why would you need VALUE()?**

When numbers are imported from other systems they are stored as text — Excel shows them left-aligned with a green triangle. SUM and math formulas return 0 on these. VALUE() converts them to real numbers.

---

**Q5. How do you add a line break inside a cell formula?**

Use `CHAR(10)` in the formula and enable Wrap Text on the cell:
```excel
=A2 & CHAR(10) & B2
```

---

**Q6. How would you extract the domain from an email address?**

```excel
=MID(A2, FIND("@",A2)+1, LEN(A2))
```
Finds the position of `@`, then extracts everything after it.

---

**Q7. How do you fully clean data imported from an external system?**

```excel
=PROPER(TRIM(CLEAN(A2)))
```
CLEAN removes invisible non-printable characters → TRIM removes extra spaces → PROPER fixes case.

---

**Q8. How do you concatenate a number with text and keep the number formatted?**

You must use TEXT() to control the number format, otherwise Excel pastes raw decimals:
```excel
="Loan amount: " & TEXT(B2, "₹#,##0")    → Loan amount: ₹50,000
```

---

## 📊 Quick Reference Table

| Formula | Purpose | Key Argument |
|---|---|---|
| `UPPER(text)` | Convert to UPPERCASE | text |
| `LOWER(text)` | Convert to lowercase | text |
| `PROPER(text)` | Capitalize Each Word | text |
| `LEFT(text, n)` | Extract from start | text, num_chars |
| `RIGHT(text, n)` | Extract from end | text, num_chars |
| `MID(text, start, n)` | Extract from middle | text, start_num, num_chars |
| `LEN(text)` | Count characters | text |
| `FIND(find, within)` | Position — case-sensitive | find_text, within_text |
| `SEARCH(find, within)` | Position — case-insensitive + wildcards | find_text, within_text |
| `EXACT(t1, t2)` | Exact case-sensitive compare | text1, text2 |
| `TRIM(text)` | Remove extra spaces | text |
| `CLEAN(text)` | Remove hidden characters | text |
| `SUBSTITUTE(text, old, new)` | Replace by value | text, old_text, new_text |
| `REPLACE(text, start, n, new)` | Replace by position | text, start, chars, new |
| `CONCATENATE / CONCAT / &` | Join strings | text1, text2, ... |
| `TEXTJOIN(delim, ignore, range)` | Join range with delimiter | delimiter, ignore_empty, range |
| `REPT(text, n)` | Repeat text | text, number_times |
| `TEXT(value, format)` | Number → formatted text | value, format_code |
| `VALUE(text)` | Text → number | text |
| `CHAR(n)` | ASCII code → character | number |
| `CODE(text)` | Character → ASCII code | text |

---

## 📁 Repository Structure

```
📁 excel-learning/
├── 01-home-tab/
│   └── README.md
├── 02-text-formulas/
│   └── README.md          ← You are here
└── assets/
    └── excel_text_formulas_cheatsheet.jpg
```

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

*Learning in public. Building in public. One formula at a time.* 🚀