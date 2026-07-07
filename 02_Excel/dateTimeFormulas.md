# 📅 Excel Date & Time Formulas — Complete Reference

> **Madanmohan Tiwari** | IT Analyst → AI-Powered Data Analyst  
> Sindhuja Microcredit, Gurugram | June 2026

Complete reference for all Excel date and time formulas — with syntax, examples, real-world loan & reporting use cases, and interview Q&A.

---

## 📋 Table of Contents

- [How Excel stores dates](#-how-excel-stores-dates)
- [Category 1 — Get Today & Now](#category-1--get-today--now)
- [Category 2 — Extract Date Parts](#category-2--extract-date-parts)
- [Category 3 — Date Math & Difference](#category-3--date-math--difference)
- [Category 4 — Weekday & Week Number](#category-4--weekday--week-number)
- [Category 5 — Working Days](#category-5--working-days)
- [Category 6 — Time Formulas](#category-6--time-formulas)
- [Power Combinations](#-power-combinations--real-world-formulas)
- [Interview Q&A](#-interview-qa)
- [Quick Reference Table](#-quick-reference-table)

---

## 💡 How Excel Stores Dates

Excel stores every date as a **serial number**. January 1, 1900 = 1. June 7, 2026 = 46179. The date you see is just formatted display — which is why you can do math directly on dates.

```excel
=A2 - B2        → number of days between two dates
=TODAY() + 30   → date 30 days from now
```

---

## Category 1 — Get Today & Now

### `TODAY()`
Returns today's date. Updates automatically every time the file recalculates.

```excel
=TODAY()                      → 07-Jun-2026
=TODAY()+30                   → 30 days from today
=TODAY()-A2                   → days since date in A2
```

> ⚠️ TODAY() is **volatile** — recalculates every time the file opens or edits. Use `Ctrl+;` to paste a static date that won't change.

---

### `NOW()`
Returns current date AND time. Also volatile.

```excel
=NOW()                        → 07-Jun-2026 14:35
=INT(NOW())                   → date only (strips time)
=NOW()-INT(NOW())             → time only (decimal fraction of day)
```

---

### `DATE(year, month, day)`
Creates a date from three separate numbers.

```excel
=DATE(2026, 6, 7)             → 07-Jun-2026
=DATE(YEAR(A2), MONTH(A2), 1) → first day of same month as A2
=DATE(YEAR(A2), MONTH(A2)+1, 0) → last day of current month
```

---

### `DATEVALUE(date_text)`
Converts a date stored as text to a serial number Excel can calculate with.

```excel
=DATEVALUE("07-Jun-2026")     → 46179  (then format as date)
=DATEVALUE(A2)                → fix imported text dates
```

---

## Category 2 — Extract Date Parts

### `DAY(date)` / `MONTH(date)` / `YEAR(date)`

```excel
=DAY(TODAY())                 → 7
=MONTH(TODAY())               → 6
=YEAR(TODAY())                → 2026
```

**Quarter of the year:**
```excel
=INT((MONTH(A2)-1)/3)+1       → 1, 2, 3, or 4
="Q" & INT((MONTH(A2)-1)/3)+1 & "-" & YEAR(A2)  → Q2-2026
```

**First day of current month:**
```excel
=DATE(YEAR(TODAY()), MONTH(TODAY()), 1)
```

---

## Category 3 — Date Math & Difference

### `DATEDIF(start_date, end_date, unit)`
Calculates exact difference between two dates. Hidden function — no autocomplete but works perfectly.

```excel
=DATEDIF(A2, TODAY(), "Y")    → complete years (age)
=DATEDIF(A2, TODAY(), "M")    → complete months
=DATEDIF(A2, TODAY(), "D")    → total days
=DATEDIF(A2, TODAY(), "YM")   → months ignoring years
=DATEDIF(A2, TODAY(), "MD")   → days ignoring months
```

| Unit | Returns |
|---|---|
| "Y" | Complete years |
| "M" | Complete months |
| "D" | Total days |
| "YM" | Months, ignoring years |
| "MD" | Days, ignoring months and years |
| "YD" | Days, ignoring years |

**Age in years and months:**
```excel
=DATEDIF(DOB,TODAY(),"Y") & " yrs " & DATEDIF(DOB,TODAY(),"YM") & " months"
```

---

### `DAYS(end_date, start_date)`
Simple day count between two dates.

```excel
=DAYS(TODAY(), A2)            → same as =TODAY()-A2
=DAYS(B2, A2)
```

---

### `EDATE(start_date, months)`
Date exactly n months in the future (positive) or past (negative).

```excel
=EDATE(A2, 6)                 → 6 months after A2  (same day)
=EDATE(A2, 12)                → 1 year after A2
=EDATE(A2, -3)                → 3 months before A2
```

> **Use case:** Loan due dates, EMI schedule, renewal reminders.

---

### `EOMONTH(start_date, months)`
Last day of the month, n months away.

```excel
=EOMONTH(TODAY(), 0)          → last day of current month
=EOMONTH(TODAY(), 1)          → last day of next month
=EOMONTH(TODAY(), -1)         → last day of last month
=EOMONTH(A2, 0)+1             → first day of next month
```

---

## Category 4 — Weekday & Week Number

### `WEEKDAY(date, [return_type])`
Day of week as a number.

```excel
=WEEKDAY(TODAY(), 1)          → 1=Sun, 7=Sat  (default)
=WEEKDAY(TODAY(), 2)          → 1=Mon, 7=Sun  (ISO standard)
```

**Check if date is a weekend:**
```excel
=WEEKDAY(A2, 2)>=6            → TRUE if Saturday or Sunday
```

---

### `WEEKNUM(date)`
Week number of the year.

```excel
=WEEKNUM(TODAY())             → 23
=WEEKNUM(A2, 21)              → ISO week number (Monday start)
```

---

### `TEXT` for day and month names

```excel
=TEXT(TODAY(), "DDDD")        → Sunday      (full day name)
=TEXT(TODAY(), "DDD")         → Sun         (short)
=TEXT(TODAY(), "MMMM")        → June        (full month name)
=TEXT(TODAY(), "MMM")         → Jun         (short)
=TEXT(TODAY(), "MMM-YYYY")    → Jun-2026
=TEXT(TODAY(), "DD/MM/YYYY")  → 07/06/2026
```

---

## Category 5 — Working Days

### `NETWORKDAYS(start_date, end_date, [holidays])`
Counts working days between two dates. Excludes weekends and optional holidays.

```excel
=NETWORKDAYS(A2, B2)          → working days, no holidays
=NETWORKDAYS(A2, B2, H2:H10)  → excludes holidays in H2:H10
=NETWORKDAYS(TODAY(), Deadline) → working days to deadline
```

---

### `WORKDAY(start_date, days, [holidays])`
Returns the date after n working days.

```excel
=WORKDAY(TODAY(), 30)         → date 30 working days from today
=WORKDAY(A2, 5, H2:H10)      → 5 working days after A2, minus holidays
=WORKDAY(TODAY(), -10)        → 10 working days before today
```

---

### `NETWORKDAYS.INTL` / `WORKDAY.INTL`
Custom weekend definition — useful in India where Saturdays may be working days.

```excel
=NETWORKDAYS.INTL(A2, B2, 11)  → Sunday-only weekend
=WORKDAY.INTL(TODAY(), 30, 11) → 30 days, Sunday only as weekend
```

| Code | Weekend |
|---|---|
| 1 | Saturday + Sunday (default) |
| 11 | Sunday only |
| 17 | Saturday only |

---

## Category 6 — Time Formulas

### `HOUR(time)` / `MINUTE(time)` / `SECOND(time)`

```excel
=HOUR(NOW())                  → 14
=MINUTE(NOW())                → 35
=SECOND(NOW())                → 22
```

---

### `TIME(hour, minute, second)`
Creates a time value from parts.

```excel
=TIME(14, 30, 0)              → 2:30:00 PM
=A2 + TIME(2, 0, 0)           → adds 2 hours to time in A2
```

---

### `TIMEVALUE(time_text)`
Converts text to a time decimal.

```excel
=TIMEVALUE("14:30")           → 0.604167  (14.5 / 24)
```

---

### Time difference

```excel
=B2-A2                        → raw difference (format as [h]:mm)
=(B2-A2)*24                   → hours as decimal number
=(B2-A2)*1440                 → total minutes
=(B2-A2)*86400                → total seconds
```

> ⚠️ Use format `[h]:mm` (with square brackets) — NOT `h:mm`. Without brackets, differences over 24 hours wrap around to 0.

---

## ⚡ Power Combinations — Real-World Formulas

### Loan portfolio & collections
```excel
Age from date of birth:
=DATEDIF(DOB_col, TODAY(), "Y")

Days since disbursement:
=TODAY()-Disbursement_Date

Loan due date (6 months from sanction):
=EDATE(Sanction_Date, 6)

Flag overdue loans:
=IF(Due_Date < TODAY(), "Overdue", "On Track")

Days overdue (0 if not overdue):
=IF(Due_Date < TODAY(), TODAY()-Due_Date, 0)

30-day repayment window check:
=AND(Payment_Date >= Cycle_Start, Payment_Date <= EDATE(Cycle_Start,1))

Workdays to collection deadline:
=NETWORKDAYS(TODAY(), Collection_Deadline)
```

### Reporting & grouping
```excel
Month-Year label for pivot grouping:
=TEXT(Date_col, "MMM-YYYY")           → Jun-2026

Quarter label:
="Q" & INT((MONTH(Date_col)-1)/3)+1 & "-" & YEAR(Date_col)  → Q2-2026

First day of current month:
=DATE(YEAR(TODAY()), MONTH(TODAY()), 1)

Last day of current month:
=EOMONTH(TODAY(), 0)

First day of next month:
=EOMONTH(TODAY(), 0)+1

Same month as today check:
=MONTH(A2)=MONTH(TODAY())
```

### Day & week analysis
```excel
Day name:         =TEXT(A2, "DDDD")          → Sunday
Is weekend:       =WEEKDAY(A2, 2)>=6          → TRUE if Sat/Sun
Week number:      =WEEKNUM(A2)
Day number ISO:   =WEEKDAY(A2, 2)             → 1=Mon to 7=Sun
```

### Time tracking
```excel
Time worked (hours as number):
=(Check_Out - Check_In)*24

Add 2 hours to a time:
=A2 + TIME(2,0,0)

Total hours over 24 (format cell as [h]:mm):
=SUM(C2:C30)   → format column as [h]:mm
```

---

## 🎯 Interview Q&A

**Q1. How does Excel store dates internally?**

Excel stores dates as serial numbers. January 1, 1900 = 1. June 7, 2026 = 46179. The date display is just formatting. This is why you can subtract two dates to get the number of days between them.

---

**Q2. What is the difference between TODAY() and NOW()?**

TODAY() returns only the current date and updates daily. NOW() returns date and time and updates on every recalculation. Both are volatile — avoid them in cells where you need a frozen timestamp. Use `Ctrl+;` to paste a static date.

---

**Q3. What is DATEDIF and why doesn't it show in autocomplete?**

DATEDIF is a legacy/hidden function inherited from Lotus 1-2-3. It works correctly but Microsoft never added it to the function library or autocomplete. Type it manually. Unit codes: "Y", "M", "D", "YM", "MD", "YD".

---

**Q4. What is the difference between EDATE and EOMONTH?**

EDATE returns the same day n months later (`=EDATE(A2, 1)` → same date, next month). EOMONTH returns the last day of the month n months away. Use `=EOMONTH(A2, 0)+1` to get the first day of the next month.

---

**Q5. What is the difference between NETWORKDAYS and WORKDAY?**

NETWORKDAYS **counts** the working days between two dates. WORKDAY **returns the date** that is n working days after a start date. Both exclude weekends and optional holidays.

---

**Q6. How do you get the quarter from a date?**

```excel
=INT((MONTH(A2)-1)/3)+1
```
Divides the month by 3, takes the integer part, adds 1. Returns 1 through 4.

---

**Q7. How do you calculate time difference in hours?**

```excel
=(End_Time - Start_Time) * 24
```
Multiply by 24 because Excel time is stored as a fraction of a day (1.0 = 24 hours). Format the result as a number.

---

**Q8. What is the difference between `h:mm` and `[h]:mm` cell format?**

`h:mm` wraps after 24 hours — 25 hours shows as `1:00`. `[h]:mm` keeps counting — 25 hours shows as `25:00`. Always use `[h]:mm` for cumulative time differences.

---

## 📊 Quick Reference Table

| Formula | Purpose | Key Note |
|---|---|---|
| `TODAY()` | Today's date | Volatile, updates daily |
| `NOW()` | Date + time | Volatile, updates on recalc |
| `DATE(y,m,d)` | Build date from parts | Good for dynamic references |
| `DATEVALUE(text)` | Text → date serial | Fix imported text dates |
| `DAY(date)` | Extract day (1–31) | — |
| `MONTH(date)` | Extract month (1–12) | — |
| `YEAR(date)` | Extract year | — |
| `DATEDIF(s,e,unit)` | Exact date difference | Hidden, no autocomplete |
| `DAYS(end,start)` | Day count | Same as `end-start` |
| `EDATE(date,months)` | n months later/earlier | Same day, different month |
| `EOMONTH(date,months)` | Last day of month | +1 for first of next month |
| `WEEKDAY(date,type)` | Day of week number | Type 2 = Mon=1, Sun=7 |
| `WEEKNUM(date)` | Week of year | ISO: use type 21 |
| `TEXT(date,"DDDD")` | Day name as text | "MMMM" for month name |
| `NETWORKDAYS(s,e)` | Count working days | Excludes weekends+holidays |
| `WORKDAY(s,n)` | Date after n workdays | 3rd arg for holidays |
| `NETWORKDAYS.INTL` | Custom weekend | Code 11 = Sunday only |
| `HOUR / MINUTE / SECOND` | Extract time parts | — |
| `TIME(h,m,s)` | Build a time value | — |
| `(B2-A2)*24` | Hours between times | Format result as number |

---

## 📁 Repository Structure

```
📁 excel-learning/
├── 01-home-tab/
├── 02-text-formulas/
├── 03-number-formulas/
├── 04-date-time-formulas/
│   └── README.md          ← You are here
└── assets/
    └── excel_date_time_formulas.jpg
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
