# SQL Prerequisites — Interview Notes

> Goal: when the interviewer asks, you give a confident 2-3 line answer — no textbook definitions.

---

## 1. Database

**Say this:** "A database is an organized collection of data that lets you store, retrieve, and manage data efficiently — instead of relying on flat files or spreadsheets."

**Follow-up:** *Why not just use files?*
→ Files lack concurrency control, security, and fast querying. A database uses indexing and query engines to fetch data in milliseconds.

---

## 2. DBMS

**Say this:** "A DBMS is software that manages a database — it handles storing, retrieving, securing, and allowing multiple users to access data safely."

**Follow-up:** *Examples?*
→ MySQL, PostgreSQL, MongoDB, Oracle.

---

## 3. RDBMS

**Say this:** "An RDBMS is a DBMS where data is stored in tables (rows and columns), and relationships between tables are defined using keys. It follows Codd's relational model."

**Follow-up (DBMS vs RDBMS — the real differentiator interviewers want):**
→ DBMS doesn't enforce relationships and data can even be stored as flat/hierarchical files. RDBMS enforces data integrity through tables, keys, and constraints, and follows ACID properties.
→ Example: A file system is a weak form of data management; MongoDB is a DBMS but not RDBMS (no fixed schema/relations); MySQL/PostgreSQL are RDBMS.

---

## 4. Tables, Rows & Columns

**Say this:** "A table represents an entity (like Employee). A row is a single record (one employee's full data), and a column is an attribute (Name, Salary, Department)."

**One-liner:** Table = entity, Row = record/tuple, Column = field/attribute.

---

## 5. Keys

**Say this:** "Keys are used to uniquely identify each row in a table and to link tables to each other."

| Key | Interview line |
|---|---|
| **Primary Key** | A column (or combination) that uniquely identifies every row, can't be NULL, and only one PK per table. |
| **Foreign Key** | A column in one table that references the Primary Key of another table — used to build relationships. |
| **Candidate Key** | All columns eligible to become a Primary Key (unique + not null). One becomes the PK, the rest become alternate keys. |
| **Composite Key** | When a single column can't guarantee uniqueness, two or more columns are combined to form the PK. |
| **Unique Key** | Similar to PK but allows one NULL, and a table can have multiple unique keys. |
| **Super Key** | Candidate key plus extra columns — any combination that guarantees uniqueness, even with unnecessary extra columns. |

**Trap question:** *PK vs Unique Key?*
→ PK: no NULL allowed, only one per table. Unique Key: one NULL allowed, multiple allowed per table.

---

## 6. Constraints

**Say this:** "Constraints are rules applied on table columns to prevent invalid data from being inserted — they enforce data integrity."

| Constraint | When to mention it |
|---|---|
| `NOT NULL` | Column can't be empty |
| `UNIQUE` | No duplicate values allowed |
| `PRIMARY KEY` | NOT NULL + UNIQUE, identifies the row |
| `FOREIGN KEY` | Referential integrity — value must match a valid row in the referenced table |
| `CHECK` | Custom condition, like `Age > 18` |
| `DEFAULT` | Sets a default value when none is provided |

**Strong line to drop:** "Constraints reject bad data at the database level itself, so you don't have to rely on application code for validation."

---

## 7. Relationships

**Say this:** "A relationship defines how two tables are connected — usually through foreign keys."

| Type | Quick example |
|---|---|
| **One-to-One** | One Employee has exactly one Passport |
| **One-to-Many** | One Department has multiple Employees |
| **Many-to-Many** | One Student can enroll in multiple Courses, and one Course can have multiple Students — needs a junction/bridge table (e.g. StudentCourse) |

**Trap question:** *How do you implement Many-to-Many?*
→ It can't be done directly — you create an associative/junction table that holds the primary keys of both tables as foreign keys.

---

## 8. Data Types

**Say this:** "The data type decides what kind of data a column can store and how much memory gets allocated."

Quick categories to rattle off:
- **Numeric:** `INT`, `BIGINT`, `DECIMAL/NUMERIC` (for money — exact precision), `FLOAT` (approximate)
- **String:** `CHAR` (fixed length), `VARCHAR` (variable length)
- **Date/Time:** `DATE`, `DATETIME`, `TIMESTAMP`
- **Boolean:** `BOOLEAN`

**Trap question:** *CHAR vs VARCHAR?*
→ CHAR is fixed length — even a small value gets padded with spaces (fast, fixed storage). VARCHAR is variable length — it only uses as much space as the data needs (storage-efficient).

**Trap question:** *Why DECIMAL over FLOAT for money?*
→ FLOAT is approximate and causes rounding errors. DECIMAL gives exact precision — always use DECIMAL for salary/price fields.

---

## 9. Normalization (1NF, 2NF, 3NF, BCNF)

**Say this (opening line):** "Normalization is the process of organizing data to reduce redundancy and avoid data anomalies — insert, update, and delete anomalies."

| Form | What it fixes, in one line |
|---|---|
| **1NF** | Every column holds atomic values (no multiple values in one cell), no repeating groups. |
| **2NF** | 1NF + no non-key column depends on only part of a composite primary key (partial dependency). |
| **3NF** | 2NF + no non-key column depends on another non-key column (no transitive dependency). |
| **BCNF** | Stricter version of 3NF — every determinant must itself be a candidate key. |

**Real interview move — keep an example ready:**
"If an Orders table repeats CustomerName and CustomerCity for every order, that's redundancy — normalization means pulling Customer into a separate table and linking it back with just a CustomerID foreign key."

**Trap question:** *When do you denormalize?*
→ In read-heavy systems (reporting/analytics/dashboards), you deliberately allow some redundancy to reduce joins and improve read speed. Mentioning this trade-off — integrity vs. performance — is what impresses interviewers.

---

## 10. ER Diagram

**Say this:** "An ER Diagram is the visual blueprint of a database design — it shows Entities (tables), Attributes (columns), and Relationships (how tables connect), before any coding happens."

Quick components:
- **Entity** → rectangle (table, e.g. Employee)
- **Attribute** → oval (column, e.g. Name, Salary)
- **Relationship** → diamond (e.g. "works in")
- **Cardinality** → shows 1:1, 1:M, M:M on the connecting lines

**Strong line to drop:** "Designing the ER diagram first means normalization and relationships are already clear, so you avoid redesigning the schema later."

---

## Quick-fire round (30-second recall before an interview)

1. DBMS vs RDBMS → Relationships + ACID + tables
2. PK vs Unique Key → NULL rule + count per table
3. CHAR vs VARCHAR → fixed vs variable storage
4. 1NF vs 2NF vs 3NF → atomic → partial dependency → transitive dependency
5. Normalization vs Denormalization → integrity vs read performance
6. M:M relationship → junction table
7. FLOAT vs DECIMAL → approximate vs exact (money = DECIMAL)

