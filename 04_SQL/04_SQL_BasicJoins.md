# Day 4 – SQL Joins (PostgreSQL) — Interview Notes

> Goal: when the interviewer asks, you give a confident 2-3 line answer, backed by a query example — no textbook definitions.

**Sample schema used throughout this file:**
```sql
employees(employee_id, first_name, department_id, salary, manager_id)
departments(department_id, department_name)
```

---

## 1. Introduction to Joins

**Say this:** "A join combines rows from two or more tables based on a related column — usually a foreign key pointing to a primary key. It exists because normalized databases split data across tables to avoid redundancy, so you need joins to bring related data back together for reporting."

```sql
SELECT e.first_name, d.department_name
FROM employees e
JOIN departments d ON e.department_id = d.department_id;
```

**Trap question:** *Why do we even normalize and then join instead of storing everything in one table?*
→ Normalization avoids redundancy and update anomalies (as covered in Day 1). Joins are the cost we accept at query time to get that data integrity — it's a trade-off between storage/integrity and query complexity.

---

## 2. Why No Join Is Sometimes Not Enough

**Say this:** "A single table often can't answer a business question because the data you need is split across tables by design. For example, you can't get 'employee name + their department name' from the `employees` table alone if department names live in a separate `departments` table — you only have `department_id` there."

```sql
-- This alone is incomplete — you only get the ID, not the readable name
SELECT first_name, department_id FROM employees;

-- You need the join to get business-readable output
SELECT e.first_name, d.department_name
FROM employees e
JOIN departments d ON e.department_id = d.department_id;
```

**Say this to sound senior:** "Whenever a question needs columns from two different entities — like 'orders with customer names' or 'employees with their manager's name' — that's your signal a join is required, not a subquery scalar lookup."

---

## 3. INNER JOIN

**Say this:** "`INNER JOIN` returns only the rows that have a match in both tables — if an employee has no matching department, or a department has no employees, those rows are excluded."

```sql
SELECT e.first_name, d.department_name, e.salary
FROM employees e
INNER JOIN departments d ON e.department_id = d.department_id;
```

**Complex example (INNER JOIN + aggregation):**
```sql
-- Average salary per department, only for departments that have employees
SELECT d.department_name, AVG(e.salary) AS avg_salary, COUNT(e.employee_id) AS headcount
FROM employees e
INNER JOIN departments d ON e.department_id = d.department_id
GROUP BY d.department_name
HAVING COUNT(e.employee_id) > 3
ORDER BY avg_salary DESC;
```

**Trap question:** *Is `JOIN` the same as `INNER JOIN`?*
→ Yes — `JOIN` defaults to `INNER JOIN` in PostgreSQL and most engines. Writing `INNER JOIN` explicitly is just clearer intent for readability.

---

## 4. LEFT JOIN

**Say this:** "`LEFT JOIN` returns all rows from the left table, plus matching rows from the right table — if there's no match, the right table's columns come back as `NULL`. It's used when you don't want to lose left-table records just because they don't have a related row."

```sql
-- All employees, even those not yet assigned a department
SELECT e.first_name, d.department_name
FROM employees e
LEFT JOIN departments d ON e.department_id = d.department_id;
```

**Complex example (LEFT JOIN to find unmatched rows — extremely common interview pattern):**
```sql
-- Employees with NO department assigned
SELECT e.first_name, e.department_id
FROM employees e
LEFT JOIN departments d ON e.department_id = d.department_id
WHERE d.department_id IS NULL;
```

**Say this to impress:** "The `LEFT JOIN ... WHERE right_table.key IS NULL` pattern is my go-to for finding orphaned or unmatched records — like customers with no orders, or products with no sales."

---

## 5. RIGHT JOIN

**Say this:** "`RIGHT JOIN` is the mirror of `LEFT JOIN` — it returns all rows from the right table, plus matches from the left, with `NULL` where there's no match. In practice, most people avoid `RIGHT JOIN` and just rewrite it as a `LEFT JOIN` by swapping table order, for consistency and readability."

```sql
-- All departments, even ones with zero employees
SELECT e.first_name, d.department_name
FROM employees e
RIGHT JOIN departments d ON e.department_id = d.department_id;

-- Same result, rewritten as LEFT JOIN (preferred style)
SELECT e.first_name, d.department_name
FROM departments d
LEFT JOIN employees e ON e.department_id = d.department_id;
```

**Trap question:** *Why do teams avoid RIGHT JOIN in style guides?*
→ It's functionally identical to a `LEFT JOIN` with tables swapped, but reading a long query with mixed `LEFT`/`RIGHT` joins is harder to follow. Sticking to `LEFT JOIN` only keeps the mental model consistent — "left table is always the anchor."

---

## 6. FULL JOIN

**Say this:** "`FULL JOIN` (or `FULL OUTER JOIN`) returns all rows from both tables — matched rows combined, and unmatched rows from either side padded with `NULL`."

```sql
SELECT e.first_name, d.department_name
FROM employees e
FULL JOIN departments d ON e.department_id = d.department_id;
```

**Complex example (FULL JOIN to find mismatches on both sides):**
```sql
-- Employees with no department AND departments with no employees, in one query
SELECT e.first_name, d.department_name
FROM employees e
FULL JOIN departments d ON e.department_id = d.department_id
WHERE e.employee_id IS NULL OR d.department_id IS NULL;
```

**Trap question:** *When would you actually use FULL JOIN in real work?*
→ Reconciliation tasks — comparing two datasets to find what's missing on either side, like matching a payments table against an invoices table to spot unmatched entries in both directions.

---

## 7. Join Comparison

| Join | Returns | NULLs appear when |
|---|---|---|
| **INNER JOIN** | Only matching rows from both tables | Never — non-matches are simply excluded |
| **LEFT JOIN** | All left rows + matches from right | Right table has no match |
| **RIGHT JOIN** | All right rows + matches from left | Left table has no match |
| **FULL JOIN** | All rows from both tables | Either side has no match |

**Say this in one shot (great closing summary line):** "INNER excludes non-matches, LEFT and RIGHT keep one side complete, FULL keeps both sides complete — the difference is entirely about which side's unmatched rows you refuse to lose."

---

## 8. Choosing the Right Join

**Say this:** "I pick the join based on which side's completeness the business question needs."

Decision checklist to mention in an interview:
- Need only records that exist in **both** tables → **INNER JOIN**
- Need **all** records from the main table, related data optional → **LEFT JOIN**
- Need to find records with **no relationship** on the other side → **LEFT JOIN + WHERE ... IS NULL**
- Need **everything from both sides**, matched or not (reconciliation) → **FULL JOIN**
- Almost never reach for **RIGHT JOIN** — flip the table order and use LEFT instead for consistency

---

## 9. Join Performance & Optimization

**Say this (separates you from a tutorial-level candidate):** "Join performance in Postgres comes down to whether the join columns are indexed, and how much data each side has to scan."

Key points to drop:

1. **Always index the join columns** — foreign key columns (`department_id` in `employees`) should have an index; primary keys already do by default.

2. **Filter before joining where possible** — applying `WHERE` on a filtered subquery/CTE before joining reduces the row count the join engine has to process.
   ```sql
   -- Filter employees first, then join — smaller join input
   SELECT e.first_name, d.department_name
   FROM (SELECT * FROM employees WHERE salary > 80000) e
   JOIN departments d ON e.department_id = d.department_id;
   ```

3. **Avoid joining on functions/expressions** — `ON LOWER(e.dept_code) = LOWER(d.dept_code)` disables index usage on both sides. Keep join keys clean and consistently typed/cased.

4. **Watch for join explosion (fan-out)** — joining two one-to-many relationships together in a single query duplicates rows unexpectedly. Aggregate one side first, or use a subquery, to avoid inflated `SUM`/`COUNT` results.
   ```sql
   -- WRONG: joining employees to two 1-to-many tables at once inflates counts
   -- e.g. employees JOIN projects JOIN certifications → duplicated rows

   -- RIGHT: aggregate each side separately before joining
   SELECT e.first_name, p.project_count, c.cert_count
   FROM employees e
   LEFT JOIN (SELECT employee_id, COUNT(*) AS project_count FROM projects GROUP BY employee_id) p
     ON e.employee_id = p.employee_id
   LEFT JOIN (SELECT employee_id, COUNT(*) AS cert_count FROM certifications GROUP BY employee_id) c
     ON e.employee_id = c.employee_id;
   ```

5. **Use EXPLAIN ANALYZE** to check if PostgreSQL is doing a Nested Loop, Hash Join, or Merge Join — and whether it's using an index scan or a sequential scan.
   ```sql
   EXPLAIN ANALYZE
   SELECT e.first_name, d.department_name
   FROM employees e
   JOIN departments d ON e.department_id = d.department_id;
   ```

**Strong line to drop:** "Before optimizing a slow join query, I run `EXPLAIN ANALYZE` first to see if it's actually doing a sequential scan — indexing the join key usually fixes it before I touch the query logic."

---

## 10. Real-world Business Scenarios

**Scenario 1 — Sales report with missing categories:**
```sql
-- All products, with sales if they exist, 0 if not
SELECT p.product_name, COALESCE(SUM(s.quantity), 0) AS total_sold
FROM products p
LEFT JOIN sales s ON p.product_id = s.product_id
GROUP BY p.product_name
ORDER BY total_sold DESC;
```

**Scenario 2 — Employees and their managers (self-join, common Day 4 extension):**
```sql
-- Self-join: employee name alongside their manager's name
SELECT emp.first_name AS employee_name, mgr.first_name AS manager_name
FROM employees emp
LEFT JOIN employees mgr ON emp.manager_id = mgr.employee_id;
```

**Scenario 3 — Loan/BFSI context (grounded in Sindhuja-style data):**
```sql
-- Branches with disbursed loans, including branches with zero disbursements this month
SELECT b.branch_name, COALESCE(SUM(l.disbursed_amount), 0) AS total_disbursed
FROM branches b
LEFT JOIN loans l ON b.branch_id = l.branch_id
  AND l.disbursement_date >= '2026-07-01'
GROUP BY b.branch_name
ORDER BY total_disbursed DESC;
```

**Scenario 4 — Reconciliation (FULL JOIN in practice):**
```sql
-- Payments recorded that have no matching invoice, and invoices with no payment
SELECT COALESCE(p.invoice_id, i.invoice_id) AS invoice_id,
       p.amount_paid, i.amount_due
FROM payments p
FULL JOIN invoices i ON p.invoice_id = i.invoice_id
WHERE p.invoice_id IS NULL OR i.invoice_id IS NULL;
```

---

## 11. Interview Questions

**Q1: What's the difference between JOIN and subquery — when would you use one over the other?**
→ A join combines row-level data from two tables side by side in one result set. A subquery is often used for a single scalar check or a filtered list (`WHERE id IN (subquery)`). Joins are typically faster and preferred when you need columns from both tables in the output; subqueries are cleaner when you only need to filter based on another table's data, not display its columns.

**Q2: Can you join more than two tables?**
→ Yes — chain multiple `JOIN` clauses, each with its own `ON` condition. Order matters for readability, not correctness (the optimizer decides actual join order internally).
```sql
SELECT e.first_name, d.department_name, p.project_name
FROM employees e
JOIN departments d ON e.department_id = d.department_id
JOIN projects p ON e.employee_id = p.employee_id;
```

**Q3: What happens if you forget the ON condition (or use a comma join)?**
→ You get a Cartesian product — every row from table A paired with every row from table B. On real tables, this creates a huge, mostly meaningless result set and can crash performance.
```sql
-- Cartesian product — 100 employees x 10 departments = 1000 rows, mostly wrong
SELECT e.first_name, d.department_name FROM employees e, departments d;
```

**Q4: LEFT JOIN with a WHERE condition on the right table — why does it sometimes behave like an INNER JOIN?**
→ If the `WHERE` clause filters on a right-table column (`WHERE d.department_name = 'IT'`), any row where the right side is `NULL` (unmatched) gets eliminated by that condition — since `NULL = 'IT'` is `UNKNOWN`, not `TRUE`. To keep it a true LEFT JOIN behavior, move that condition into the `ON` clause instead.
```sql
-- Behaves like INNER JOIN — unmatched rows get filtered out
SELECT e.first_name, d.department_name
FROM employees e
LEFT JOIN departments d ON e.department_id = d.department_id
WHERE d.department_name = 'IT';

-- True LEFT JOIN behavior — condition moved to ON
SELECT e.first_name, d.department_name
FROM employees e
LEFT JOIN departments d ON e.department_id = d.department_id AND d.department_name = 'IT';
```

**Q5: How would you find departments with no employees?**
→ `LEFT JOIN` from `departments` to `employees`, then filter `WHERE employee.id IS NULL`.
```sql
SELECT d.department_name
FROM departments d
LEFT JOIN employees e ON d.department_id = e.department_id
WHERE e.employee_id IS NULL;
```

**Q6: Difference between UNION and JOIN?**
→ `JOIN` combines columns side by side (horizontally) based on a related key. `UNION` stacks rows on top of each other (vertically) from queries with the same column structure — no key relationship needed.

---

## 12. Practice Exercises

Try writing these yourself against the `employees` / `departments` schema (and imagine a `projects(project_id, project_name, employee_id)` table too):

1. List all employees along with their department name. Include employees with no department.
2. Find all departments that currently have zero employees.
3. Find the total salary paid out per department, sorted highest to lowest, only for departments with more than 2 employees.
4. Write a self-join query to list each employee with their manager's name; show `'No Manager'` instead of NULL for top-level employees (hint: `COALESCE`).
5. Find employees who are NOT assigned to any project (LEFT JOIN + IS NULL pattern).
6. Write a FULL JOIN query between `employees` and `projects` to find employees without a project AND projects without an assigned employee, in a single result set.
7. Rewrite a query that currently uses a comma join (`FROM employees e, departments d WHERE e.department_id = d.department_id`) into a proper explicit `INNER JOIN`.

---

## Quick-fire round (30-second recall before an interview)

1. INNER JOIN → only matches, both sides
2. LEFT JOIN → all left + matches, NULL for unmatched right
3. RIGHT JOIN → mirror of LEFT, rarely used in practice
4. FULL JOIN → everything from both sides, NULLs on either side
5. Find unmatched rows → `LEFT JOIN ... WHERE right.key IS NULL`
6. Comma join with no condition → Cartesian product, avoid it
7. WHERE on right-table column after LEFT JOIN → silently becomes INNER JOIN; put condition in ON instead
8. Fan-out risk → aggregate each side separately before joining two 1-to-many tables together
