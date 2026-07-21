# Day 3 – WHERE Clause Deep Dive (PostgreSQL) — Interview Notes

> Goal: when the interviewer asks, you give a confident 2-3 line answer, backed by a query example — no textbook definitions.

---

## WHERE Clause

**Say this:** "`WHERE` filters individual rows based on a condition before any grouping happens — only rows that evaluate to `TRUE` are returned. It runs right after `FROM` in the logical execution order."

```sql
SELECT employee_id, first_name, department, salary
FROM employees
WHERE salary > 60000;
```

**Trap question:** *What happens with NULL in WHERE?*
→ Any comparison with `NULL` returns `UNKNOWN`, not `TRUE` or `FALSE` — so rows with `NULL` in the compared column are automatically excluded unless you explicitly check with `IS NULL`.

---

## Comparison Operators

**Say this:** "Comparison operators compare a column against a value — `=`, `!=` / `<>`, `>`, `<`, `>=`, `<=`. Straightforward, but the interview angle is usually `=` vs `<>`/`!=` and NULL handling."

```sql
SELECT * FROM employees WHERE department = 'IT';
SELECT * FROM employees WHERE salary >= 50000;
SELECT * FROM employees WHERE department <> 'HR';
```

**Trap question:** *`!=` vs `<>`?*
→ Both mean "not equal." `<>` is the SQL standard and more portable; `!=` is widely supported (including PostgreSQL) but not ANSI standard — prefer `<>` in production code you want portable.

---

## Logical Operators

**Say this:** "Logical operators combine multiple conditions — `AND` (both true), `OR` (either true), `NOT` (negates a condition). Operator precedence matters: `AND` is evaluated before `OR`, so always use parentheses to make intent explicit."

```sql
SELECT * FROM employees
WHERE department = 'IT' AND salary > 60000;

SELECT * FROM employees
WHERE department = 'IT' OR department = 'Finance';

SELECT * FROM employees
WHERE NOT department = 'HR';
```

**Complex example (precedence trap — a favorite interview gotcha):**
```sql
-- WITHOUT parentheses — ambiguous, AND binds tighter than OR
SELECT * FROM employees
WHERE department = 'IT' OR department = 'Finance' AND salary > 80000;
-- Actually means: department = 'IT' OR (department = 'Finance' AND salary > 80000)

-- WITH parentheses — explicit and correct intent
SELECT * FROM employees
WHERE (department = 'IT' OR department = 'Finance') AND salary > 80000;
```

**Say this to impress:** "I always wrap `OR` conditions in parentheses when mixed with `AND` — because SQL evaluates `AND` before `OR`, silent logic bugs are a common real-world mistake here."

---

## Range Operators

**Say this:** "`BETWEEN` checks if a value falls within an inclusive range — it's shorthand for `>= AND <=`, and works on numbers, dates, and even text."

```sql
SELECT * FROM employees
WHERE salary BETWEEN 40000 AND 90000;

-- Equivalent to:
SELECT * FROM employees
WHERE salary >= 40000 AND salary <= 90000;

-- Works on dates too
SELECT * FROM employees
WHERE hire_date BETWEEN '2023-01-01' AND '2023-12-31';
```

**Trap question:** *Is BETWEEN inclusive or exclusive?*
→ Inclusive on both ends — `BETWEEN 40000 AND 90000` includes both 40000 and 90000.

**Complex example (NOT BETWEEN):**
```sql
-- Employees outside the mid salary band
SELECT * FROM employees
WHERE salary NOT BETWEEN 40000 AND 90000;
```

---

## Membership Operators

**Say this:** "`IN` checks if a value matches any value in a given list — cleaner than chaining multiple `OR` conditions on the same column."

```sql
-- Instead of this:
SELECT * FROM employees
WHERE department = 'IT' OR department = 'Finance' OR department = 'HR';

-- Write this:
SELECT * FROM employees
WHERE department IN ('IT', 'Finance', 'HR');
```

**Complex example (IN with a subquery — very common in interviews):**
```sql
-- Employees who work in departments with more than 10 people
SELECT first_name, department
FROM employees
WHERE department IN (
    SELECT department
    FROM employees
    GROUP BY department
    HAVING COUNT(*) > 10
);
```

**Trap question:** *NOT IN with NULLs — classic gotcha?*
→ If the subquery/list used with `NOT IN` contains even one `NULL`, the entire result becomes empty because any comparison to `NULL` is `UNKNOWN`. Safer to use `NOT EXISTS` when the list might contain `NULL`.

```sql
-- Risky if department can be NULL in the subquery
SELECT * FROM employees
WHERE department NOT IN (SELECT department FROM archived_departments);

-- Safer alternative
SELECT * FROM employees e
WHERE NOT EXISTS (
    SELECT 1 FROM archived_departments a
    WHERE a.department = e.department
);
```

---

## Search Operators (LIKE, ILIKE)

**Say this:** "`LIKE` does pattern matching on text, case-sensitive. `ILIKE` is PostgreSQL-specific and does the same thing but case-insensitive."

```sql
-- Case-sensitive: only matches 'Amit', not 'amit' or 'AMIT'
SELECT * FROM employees WHERE first_name LIKE 'Amit';

-- Case-insensitive (PostgreSQL only)
SELECT * FROM employees WHERE first_name ILIKE 'amit';
```

**Trap question:** *LIKE vs ILIKE — when to use which?*
→ Use `ILIKE` when matching user-typed search input where case shouldn't matter (e.g. search bars). Use `LIKE` when case sensitivity is intentional, or on databases other than PostgreSQL where `ILIKE` isn't available (use `LOWER(column) LIKE LOWER(pattern)` instead for portability).

---

## Wildcards (%, _)

**Say this:** "`%` matches zero or more characters, `_` matches exactly one character — these are the building blocks for every `LIKE`/`ILIKE` pattern."

```sql
-- Starts with 'A'
SELECT * FROM employees WHERE first_name LIKE 'A%';

-- Ends with 'a'
SELECT * FROM employees WHERE first_name LIKE '%a';

-- Contains 'an' anywhere
SELECT * FROM employees WHERE first_name LIKE '%an%';

-- Exactly 5 characters, starting with 'R'
SELECT * FROM employees WHERE first_name LIKE 'R____';

-- Second character is 'a' (any first character)
SELECT * FROM employees WHERE first_name LIKE '_a%';
```

**Complex example (combining wildcards with ILIKE + other conditions):**
```sql
-- Case-insensitive search for names starting with 'sh', in IT or Finance, salary above 50k
SELECT first_name, department, salary
FROM employees
WHERE first_name ILIKE 'sh%'
  AND department IN ('IT', 'Finance')
  AND salary > 50000
ORDER BY salary DESC;
```

**Trap question:** *How to search for a literal `%` or `_` in data?*
→ Escape it: `LIKE '50\%' ESCAPE '\'` — otherwise the database treats it as a wildcard, not a literal character.

---

## Performance & Best Practices

**Say this (this is where you separate yourself from a tutorial-level answer):** "`WHERE` clause performance mostly comes down to whether the condition can use an index or forces a full table scan."

Key points to drop in an interview:

1. **Leading wildcard kills index usage:** `LIKE '%an%'` or `LIKE '%an'` can't use a standard B-tree index — the engine has to scan every row. `LIKE 'an%'` (no leading `%`) can use an index.
   ```sql
   -- Can use index (sargable)
   WHERE first_name LIKE 'An%'

   -- Cannot use a standard index (leading wildcard)
   WHERE first_name LIKE '%an%'
   ```

2. **Avoid functions on indexed columns in WHERE** — wrapping a column in a function (`LOWER(department) = 'it'`) prevents index usage unless you create a functional index. Better to store data normalized (consistent casing) or use a functional index if case-insensitive search is frequent.

3. **IN vs OR** — `IN` is more readable and the optimizer treats it the same as chained `OR`s, but `IN` scales better for large lists and is easier to generate dynamically.

4. **BETWEEN is sargable** (index-friendly) — prefer it over separate `>=` and `<=` for readability; performance is identical.

5. **Filter early, filter specific** — put the most selective condition (the one that eliminates the most rows) logically first for readability; the query planner reorders internally, but selective `WHERE` conditions combined with an index dramatically cut down rows scanned.

6. **NOT IN with nullable columns** — as covered above, prefer `NOT EXISTS` to avoid the empty-result trap.

**Strong line to drop:** "I always check whether a `WHERE` condition is sargable — meaning the engine can use an index to seek instead of scanning the whole table — because that's usually the actual bottleneck in slow queries, not the query logic itself."

---

## Quick-fire round (30-second recall before an interview)

1. WHERE vs HAVING → rows before grouping vs groups after aggregation
2. `<>` vs `!=` → `<>` is ANSI standard, both work in PostgreSQL
3. AND vs OR precedence → AND evaluated first, always parenthesize mixed conditions
4. BETWEEN → inclusive on both ends
5. NOT IN + NULL → returns empty result; use NOT EXISTS instead
6. LIKE vs ILIKE → case-sensitive vs case-insensitive (PostgreSQL only)
7. `%` vs `_` → zero-or-more chars vs exactly one char
8. Leading `%` in LIKE → kills index usage, forces full table scan
