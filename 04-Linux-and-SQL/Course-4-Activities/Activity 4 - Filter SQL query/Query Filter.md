# SQL Filtering in MariaDB — Lab Summary

## Overview

This lab focuses on using **basic SQL filters** to find specific information in a MariaDB database.

As a security analyst, being able to narrow down database results is useful because security work often involves finding a particular employee, device, department, or system without manually checking every record.

The lab uses an **organization** database containing information about employees and their machines.

---

## Database Orientation

Before writing queries, it helps to understand the structure of the tables.

```sql
DESCRIBE machines;
DESCRIBE employees;
```

`DESCRIBE` shows the structure of a table, including:

- **Field** — the column name
- **Type** — the type of data stored in the column

Think of `DESCRIBE` as a **table of contents for a database table**. It helps you remember the exact column names before writing a query.

---

# Task 1 — List All Organization Machines

The goal is to display the ID and operating system of every machine.

```sql
SELECT device_id, operating_system
FROM machines;
```

### Result

The `machines` table contains **200 records**.

### Key idea

`SELECT` lets you choose which columns you want to see instead of displaying the entire table.

---

# Task 2 — Find Machines Using OS 2

The organization needs to update all machines running **OS 2**.

```sql
SELECT device_id, operating_system
FROM machines
WHERE operating_system = 'OS 2';
```

### Result

There are **80 machines** running OS 2.

### Important SQL rules

SQL is strict about syntax:

- End every query with a **semicolon (`;`)**.
- Put text values inside **single quotes**.
- Do not put quotes around column names.

Correct:

```sql
WHERE operating_system = 'OS 2';
```

Incorrect:

```sql
WHERE operating_system = OS 2;
```

### Key idea — `WHERE`

The `WHERE` clause acts like a **filter**. It tells SQL to return only the records that match a specific condition.

---

# Task 3 — Find Employees by Department

The organization needs the office numbers of employees in the **Finance** and **Sales** departments.

## Finance

```sql
SELECT *
FROM employees
WHERE department = 'Finance';
```

The first employee returned has the employee ID:

**1003**

## Sales

Modify the query to search for Sales employees:

```sql
SELECT *
FROM employees
WHERE department = 'Sales';
```

### Result

There are **33 employees** in the Sales department.

### Key idea

The same SQL structure can be reused for different filters. Only the value being searched for needs to change.

---

# Task 4 — Identify Employees and Their Machines

A machine in office **South-109** has an issue. The goal is to identify the employee using that office.

```sql
SELECT *
FROM employees
WHERE office = 'South-109';
```

### Result

The employee using the affected computer has the user ID:

**jlansky**

---

## Find Everyone in the South Building

The team later discovers that all machines in the South building may have issues.

Instead of searching for one specific office, use the `LIKE` operator:

```sql
SELECT *
FROM employees
WHERE office LIKE 'South%';
```

### How `LIKE` and `%` work

`LIKE` is used for simple text pattern matching.

The `%` symbol works like a **fill-in-the-blanks** character. It can represent any number of characters.

| Pattern | Meaning | Example |
|---|---|---|
| `'South%'` | Starts with South | `South-109`, `South-210` |
| `'%South'` | Ends with South | `Office-South` |
| `'%South%'` | Contains South anywhere | `New-South-Office` |

For this task, `'South%'` is used because office names **start with `South`**.

### Result

The first employee listed from the South building works in the:

**Finance department**

---

# Important SQL Concepts Learned

## 1. `SELECT`

Used to choose the data you want to retrieve.

```sql
SELECT device_id, operating_system
FROM machines;
```

## 2. `WHERE`

Used to filter records based on a condition.

```sql
WHERE department = 'Finance';
```

## 3. `LIKE`

Used when you need to search for a text pattern rather than an exact value.

```sql
WHERE office LIKE 'South%';
```

## 4. `%`

A wildcard representing zero or more characters.

```sql
'South%'
```

means the text must **start with "South"**.

---

# Quick Reference

| Requirement | SQL |
|---|---|
| See table structure | `DESCRIBE table_name;` |
| Select specific columns | `SELECT column1, column2 FROM table;` |
| Filter an exact value | `WHERE column = 'value';` |
| Search a text pattern | `WHERE column LIKE 'pattern';` |
| Starts with text | `LIKE 'text%';` |
| Ends with text | `LIKE '%text';` |
| Contains text | `LIKE '%text%';` |

---

# Lab Takeaway

The main lesson from this lab is that SQL becomes much more useful when you can **filter the data instead of looking through everything manually**.

For security analysts, simple commands such as `SELECT`, `WHERE`, and `LIKE` can quickly narrow a large database down to the exact devices, employees, or departments that need attention.

## Key Results

- **200** total machines
- **80** machines running OS 2
- Finance query first returned employee ID **1003**
- **33** employees work in Sales
- The employee using **South-109** is **jlansky**
- The first employee listed in the South building belongs to **Finance**
