# Module 4 : SQL & Database Querying

## Section 1: SQL Filtering vs. Linux Filtering

### Overview & Accessing SQL

You can get to SQL in a few different ways, one of the most common being straight from the Linux command line. For example, once you run `sqlite3`, everything you type next gets routed to SQLite instead of being interpreted as a regular shell command.

So why use SQL instead of just grepping through files in Linux? A few reasons:

* **Structure** — SQL keeps records neatly separated into columns, which makes it easy to work with. Linux, on the other hand, just prints everything out as plain lines of text, so pulling out column-level insight takes a lot more manual effort.
* **Joining data** — SQL is built to join separate tables together based on shared fields. Linux has no real equivalent for this — it isn't designed to link files together in a relational way.
* **When to use which** — SQL is the better tool when you're working with structured database logs. Linux filtering still earns its keep when you're digging through raw text files that were never meant to live in a database.

---

## Section 2: Basic SQL Queries (`SELECT`, `FROM`, `ORDER BY`)

### Query Fundamentals

* **`SELECT`** tells SQL which columns you want back. For example, `SELECT customerid, city` only returns those two fields. You can also use `SELECT *` to grab every column, but be careful — on large tables this can slow things down noticeably.
* **`FROM`** points to the table you're actually querying. Every query wraps up with a semicolon (`;`).
* **Sample reference dataset** — Throughout this guide, examples pull from the *Chinook database*, a sample dataset modeled on a digital media company. It includes tables like `employees`, `customers`, and `invoices`.

### Sorting Results with `ORDER BY`

* **Ascending order (the default)** — `ORDER BY column_name` sorts numbers from smallest to largest and text alphabetically from A to Z.
* **Descending order** — Add `DESC` to flip that: `ORDER BY column_name DESC` goes largest to smallest, or Z to A.
* **Sorting by multiple columns** — SQL sorts by the first column listed, then uses the second column as a tiebreaker for rows that match on the first. For instance, `ORDER BY country, city` sorts everything by country first, then alphabetizes cities within each country.

---

## Section 3: The `WHERE` Clause & Wildcards

### Basic Filtering

The `WHERE` clause is how you set the conditions a row has to meet before it shows up in your results.

```sql
SELECT firstname, lastname, title, email
FROM employees
WHERE title = 'IT Staff';
```

### Pattern Matching (`LIKE` & Wildcards)

Sometimes you don't want an exact match — you want anything that *looks like* a certain pattern. That's what `LIKE` is for, and it works hand-in-hand with wildcards.

* **The `%` wildcard** stands in for zero, one, or many characters. So `WHERE title LIKE 'IT%'` would catch both "IT Staff" and "IT Manager."
* **The `_` wildcard** stands in for exactly one character. `WHERE state LIKE 'N_'` would match "NY," "NV," "NS," or "NT" — anything that starts with N and is exactly two characters long.

---

## Section 4: Comparison Operators & Ranges

### Numerical, Date, and Time Data

When you're doing security analysis, filtering on numbers and dates matters just as much as filtering on text — think login failure counts, timestamps in logs, or when a system was last patched.

| **Operator** | **Type**        | **Description**                                  | **Example**                                            |
| ------------ | ---------------- | ------------------------------------------------- | -------------------------------------------------------- |
| `=`          | Equality         | Exact match                                        | `WHERE title = 'IT Staff'`                                |
| `>` / `<`    | Exclusive         | Strictly greater than / less than                  | `WHERE birthdate > '1970-01-01'`                           |
| `>=` / `<=`  | Inclusive         | Greater than or equal to / less than or equal to   | `WHERE birthdate >= '1970-01-01'`                          |
| `<>` or `!=` | Negation          | Not equal to                                       | `WHERE country <> 'USA'`                                   |
| `BETWEEN`    | Inclusive Range   | Filters values that fall within a start and end     | `WHERE hiredate BETWEEN '2002-01-01' AND '2003-01-01'`      |

---

## Section 5: Logical Operators (`AND`, `OR`, `NOT`)

### Multi-Criteria Constraints

**`AND`** requires every condition you list to be true at the same time.

```sql
SELECT firstname, lastname, email, country, supportrepid
FROM customers
WHERE supportrepid = 5 AND country = 'USA';
```

**`OR`** only needs one of the conditions to be true. Note that you have to spell out the full comparison on each side — you can't shorten it.

```sql
SELECT firstname, lastname, email, country
FROM customers
WHERE country = 'Canada' OR country = 'USA';
```

**`NOT`** flips a condition, pulling back everything that *doesn't* match.

```sql
SELECT firstname, lastname, email, country
FROM customers
WHERE NOT country = 'Canada' AND NOT country = 'USA';
```

---

## Section 6: SQL Joins Comparison

| **Join Type**        | **Records Returned**                                                                                                     | **Syntax Example**                                                                        |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| **`INNER JOIN`**      | Only the rows that have a match in **both** tables on the connecting key.                                                    | `FROM employees INNER JOIN machines ON employees.device_id = machines.device_id;`             |
| **`LEFT JOIN`**       | **Every** row from the first (left) table, plus any matching rows from the second (right) table. Rows with no match on the right show up as `NULL`.  | `FROM employees LEFT JOIN machines ON employees.device_id = machines.device_id;`              |
| **`RIGHT JOIN`**      | **Every** row from the second (right) table, plus any matching rows from the first (left) table. Rows with no match on the left show up as `NULL`.   | `FROM employees RIGHT JOIN machines ON employees.device_id = machines.device_id;`             |
| **`FULL OUTER JOIN`** | **Every** record from both tables, matched or not.                                                                            | `FROM employees FULL OUTER JOIN machines ON employees.device_id = machines.device_id;`        |

One thing worth flagging: when you're pulling a column that exists in more than one joined table, you need to be specific about which table it's coming from using dot notation (`table.column`) — for example, `employees.device_id` — otherwise SQL won't know which one you mean and will throw an ambiguity error.

---

## Section 7: Aggregate Functions

Aggregate functions crunch numbers across many rows and hand you back a single summary value, rather than the individual rows themselves.

* **`COUNT()`** tells you how many non-NULL rows matched your query.
* **`AVG()`** gives you the average of the values in a column.
* **`SUM()`** adds up all the numerical values in a column.

```sql
-- Count total US customers
SELECT COUNT(firstname)
FROM customers
WHERE country = 'USA';
```
