# Day 2 – Core SQL (PostgreSQL) — Interview Notes

> Goal: when the interviewer asks, you give a confident 2-3 line answer, backed by a query example — no textbook definitions.

---

## Topic 1: Introduction to SQL

### What is SQL?

**Say this:** "SQL stands for Structured Query Language — it's used to communicate with a relational database to store, retrieve, update, and manage data."

### Why SQL is used / What SQL can do

**Say this:** "SQL lets you define the database structure, insert and modify data, query it with complex conditions, control access, and manage transactions — basically the entire lifecycle of data lives in SQL."

**Trap question:** *Is SQL a programming language?*
→ It's a declarative language — you tell it *what* result you want, not *how* to get it (unlike procedural languages). The database engine decides the execution plan.

### SQL Categories

**Say this (rattle these off fast, this is a very common opener question):**

| Category | Full form | What it does | Commands |
|---|---|---|---|
| **DQL** | Data Query Language | Fetch/read data | `SELECT` |
| **DDL** | Data Definition Language | Define/modify structure | `CREATE`, `ALTER`, `DROP`, `TRUNCATE` |
| **DML** | Data Manipulation Language | Modify data | `INSERT`, `UPDATE`, `DELETE` |
| **DCL** | Data Control Language | Control access/permissions | `GRANT`, `REVOKE` |
| **TCL** | Transaction Control Language | Manage transactions | `COMMIT`, `ROLLBACK`, `SAVEPOINT` |

**Trap question:** *Is TRUNCATE DDL or DML?*
→ It's DDL — it resets the table structure (deallocates pages) rather than deleting rows one by one, and it can't be rolled back like DML in most engines.

---

## Topic 2: SQL Query Clauses

### Basic Query Writing

**Say this:** "`SELECT` fetches columns, `FROM` tells the engine which table, and you list only the columns you need instead of `SELECT *` in production code — because `SELECT *` pulls unnecessary data and breaks if the schema changes."

```sql
-- Basic
SELECT * FROM employees;

-- Best practice: specific columns
SELECT employee_id, first_name, salary
FROM employees;
```

**Trap question:** *Why avoid `SELECT *` in production?*
→ It transfers unnecessary columns (performance hit), breaks the application if a new column is added, and ignores any index-only scan optimizations.

### Filtering — WHERE

**Say this:** "`WHERE` filters rows before grouping/aggregation happens — it works on individual rows, not on aggregated results."

```sql
SELECT employee_id, first_name, department, salary
FROM employees
WHERE department = 'IT' AND salary > 50000;
```

**Complex example (multiple conditions + pattern matching):**
```sql
SELECT employee_id, first_name, department, salary
FROM employees
WHERE (department = 'IT' OR department = 'Finance')
  AND salary BETWEEN 40000 AND 90000
  AND first_name LIKE 'A%';
```

### Sorting — ORDER BY

**Say this:** "`ORDER BY` sorts the final result set — `ASC` is default (ascending), `DESC` for descending. You can sort by multiple columns, where the first column decides primary order and the next breaks ties."

```sql
-- Single column
SELECT * FROM employees ORDER BY salary DESC;

-- Nested / multi-column
SELECT department, first_name, salary
FROM employees
ORDER BY department ASC, salary DESC;
```

**Trap question:** *Can you ORDER BY a column not in SELECT?*
→ Yes, as long as it's from the same table/join — the column doesn't have to appear in the SELECT list.

### Grouping — GROUP BY & HAVING

**Say this:** "`GROUP BY` collapses rows into groups based on a column, usually paired with aggregate functions like `SUM`, `COUNT`, `AVG`. `HAVING` filters *after* grouping — it's the `WHERE` for aggregated data, since `WHERE` can't filter on aggregate results."

```sql
-- Department-wise average salary, only departments averaging above 60000
SELECT department, COUNT(*) AS total_employees, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 60000
ORDER BY avg_salary DESC;
```

**Trap question:** *WHERE vs HAVING?*
→ `WHERE` filters rows before grouping (can't use aggregate functions). `HAVING` filters groups after aggregation (built to use aggregate functions like `SUM()`, `COUNT()`).

**Complex example (both together):**
```sql
-- Only consider active employees, then find departments with more than 5 high earners
SELECT department, COUNT(*) AS high_earners
FROM employees
WHERE status = 'active' AND salary > 70000
GROUP BY department
HAVING COUNT(*) > 5
ORDER BY high_earners DESC;
```

### Other Clauses

**DISTINCT — Say this:** "`DISTINCT` removes duplicate rows from the result set, applied across all selected columns together, not per column."

```sql
SELECT DISTINCT department FROM employees;
```

**LIMIT (PostgreSQL) — Say this:** "`LIMIT` restricts how many rows come back — commonly used with `ORDER BY` for pagination or top-N queries."

```sql
-- Top 5 highest paid employees
SELECT first_name, salary
FROM employees
ORDER BY salary DESC
LIMIT 5;

-- Pagination: page 2, 10 rows per page
SELECT first_name, salary
FROM employees
ORDER BY employee_id
LIMIT 10 OFFSET 10;
```

**Aliases (AS) — Say this:** "Aliases rename a column or table temporarily in the output, mainly for readability or to shorten table names in joins."

```sql
SELECT e.first_name AS name, e.salary AS pay
FROM employees AS e
WHERE e.salary > 50000;
```

### SQL Coding Order vs Logical Execution Order

**Say this (this is a favorite trap question — always ready):** "SQL is written in one order but executed by the engine in a different order. That's why you can't use a column alias in `WHERE` but you can in `ORDER BY`."

**Coding (writing) order:**
```
SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY → LIMIT
```

**Logical execution order:**
```
FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT
```

**Say this to really impress:** "That's exactly why `WHERE` can't reference an aggregate alias defined in `SELECT` — because `WHERE` executes before `SELECT` — but `ORDER BY` can, because it runs after `SELECT`."

```sql
-- This FAILS — alias not available yet in WHERE
SELECT salary * 12 AS annual_salary
FROM employees
WHERE annual_salary > 600000;   -- ❌ Error

-- This WORKS — ORDER BY runs after SELECT
SELECT salary * 12 AS annual_salary
FROM employees
ORDER BY annual_salary DESC;    -- ✅
```

---

## Topic 3: DDL (Data Definition Language)

### CREATE

**Say this:** "`CREATE` defines a new database object — a database, table, view, or index — it sets up structure, not data."

```sql
-- Create database
CREATE DATABASE company_db;

-- Create table
CREATE TABLE employees (
    employee_id SERIAL PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    department VARCHAR(50),
    salary DECIMAL(10,2) DEFAULT 0,
    hire_date DATE
);
```

### ALTER

**Say this:** "`ALTER` modifies the structure of an existing table without touching its data — adding/dropping/renaming columns, or changing data types."

```sql
-- Add column
ALTER TABLE employees ADD COLUMN email VARCHAR(100);

-- Drop column
ALTER TABLE employees DROP COLUMN email;

-- Rename column
ALTER TABLE employees RENAME COLUMN first_name TO full_name;

-- Change data type
ALTER TABLE employees ALTER COLUMN salary TYPE NUMERIC(12,2);

-- Rename table
ALTER TABLE employees RENAME TO staff;
```

### DROP

**Say this:** "`DROP` permanently removes the object itself — the table structure and all its data are gone, and it can't be rolled back."

```sql
DROP TABLE employees;
DROP DATABASE company_db;
```

### Comparisons

**Trap question:** *DROP vs DELETE?*
→ `DROP` removes the entire table (structure + data), is DDL, auto-commits, can't be rolled back. `DELETE` removes specific rows (data only), is DML, can use `WHERE`, and can be rolled back inside a transaction.

**Trap question:** *DROP vs TRUNCATE?*
→ `DROP` removes the table completely — structure and data both gone. `TRUNCATE` empties all rows but keeps the table structure intact so you can insert into it again immediately.

---

## Topic 4: DML (Data Manipulation Language)

### INSERT

**Say this:** "`INSERT` adds new rows into a table — single row, multiple rows in one statement, or rows copied from another table using a `SELECT`."

```sql
-- Single row
INSERT INTO employees (first_name, department, salary, hire_date)
VALUES ('Rahul', 'IT', 55000, '2024-01-15');

-- Multiple rows
INSERT INTO employees (first_name, department, salary, hire_date)
VALUES
    ('Priya', 'Finance', 62000, '2024-02-01'),
    ('Aman', 'IT', 58000, '2024-02-10');

-- INSERT ... SELECT with WHERE (copy filtered data into another table)
INSERT INTO high_earners (employee_id, first_name, salary)
SELECT employee_id, first_name, salary
FROM employees
WHERE salary > 80000;
```

### UPDATE

**Say this:** "`UPDATE` modifies existing rows — always pair it with `WHERE`, otherwise every row in the table gets updated."

```sql
UPDATE employees
SET salary = salary * 1.10
WHERE department = 'IT';
```

**Complex example (update using a subquery):**
```sql
-- Give a 5% raise to employees earning below their department's average
UPDATE employees e
SET salary = salary * 1.05
WHERE salary < (
    SELECT AVG(salary)
    FROM employees e2
    WHERE e2.department = e.department
);
```

### DELETE

**Say this:** "`DELETE` removes rows matching a condition — it's DML, so it's logged row-by-row and can be rolled back within a transaction."

```sql
DELETE FROM employees
WHERE department = 'HR' AND hire_date < '2020-01-01';
```

### TRUNCATE

**Say this:** "`TRUNCATE` removes all rows from a table instantly — faster than `DELETE` because it doesn't log individual row deletions, but it can't use `WHERE`."

```sql
TRUNCATE TABLE employees;
```

### Comparisons

**Trap question:** *DELETE vs TRUNCATE?*
→ `DELETE` removes specific rows (needs `WHERE` for that), is slower (row-by-row logging), and can be rolled back. `TRUNCATE` removes all rows at once, is faster (deallocates pages), resets identity/auto-increment counters, and in most engines can't be selectively filtered.

**Trap question — the classic 3-way (say this exact structure in interviews):**
→ "`DELETE` is DML, removes rows with a condition, rollback possible. `TRUNCATE` is DDL, removes all rows, faster, resets auto-increment, rollback depends on engine/transaction. `DROP` is DDL, removes the entire table including structure, no rollback."

### Best Practices

**Say this:** "The single biggest real-world mistake in DML is forgetting the `WHERE` clause in `UPDATE` or `DELETE` — that silently updates or deletes every row in the table. Best practice is to first run the same condition as a `SELECT` to confirm which rows are affected, then convert it to `UPDATE`/`DELETE`."

```sql
-- Step 1: Verify first
SELECT * FROM employees WHERE department = 'IT' AND salary > 90000;

-- Step 2: Only then run
DELETE FROM employees WHERE department = 'IT' AND salary > 90000;
```

**Common mistakes to mention if asked:**
- Running `UPDATE`/`DELETE` without `WHERE` → affects the whole table
- Using `TRUNCATE` when you actually needed to keep some rows (no `WHERE` support)
- Forgetting `COMMIT` after DML inside a transaction, leaving changes uncommitted
- Not wrapping bulk `UPDATE`/`DELETE` in a transaction, so a failure midway leaves data half-changed

---

## Quick-fire round (30-second recall before an interview)

1. SQL categories → DQL (read), DDL (structure), DML (data), DCL (access), TCL (transactions)
2. WHERE vs HAVING → before grouping (rows) vs after grouping (aggregates)
3. Coding order vs Execution order → FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT
4. DROP vs DELETE vs TRUNCATE → structure+data / rows with condition / all rows fast
5. INSERT ... SELECT → copy filtered data across tables in one statement
6. Golden rule → always `SELECT` with the same `WHERE` before running `UPDATE`/`DELETE`
