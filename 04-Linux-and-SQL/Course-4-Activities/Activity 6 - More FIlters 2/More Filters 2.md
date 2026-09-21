# Activity: Filter Queries Using AND, OR, and NOT Operators

## Activity Overview

In this activity, I worked as a security analyst using SQL to find specific groups of records from an organization's database. Since security investigations often require more than one condition, I used the logical operators `AND`, `OR`, and `NOT` along with `LIKE` to make my searches more precise.

The queries helped me investigate failed login attempts, check activity on specific dates, identify logins from outside a particular country, and find employees who needed software updates.

---

## Scenario

The security operations team needed information from two tables: `log_in_attempts` and `employees`.

I had to answer several different questions, such as:

- Which login attempts failed after business hours?
- What logins happened on specific dates?
- Which login attempts came from outside Mexico?
- Which Marketing employees work in the East building?
- Which employees work in Finance or Sales?
- Which employees are not part of the IT department?

I used different SQL logical operators to handle each requirement.

---

## Tasks & SQL Solutions

### Task 1: Find Failed Login Attempts After Business Hours

The team wanted to investigate failed login attempts that happened after normal working hours, specifically after 18:00.

In MySQL/MariaDB, the `success` column uses `1` for a successful login and `0` for a failed login.

**SQL Query:**

```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00:00'
  AND success = 0;
```

**What I learned:**

- `AND` means that both conditions must be true.
- In this case, the login had to happen after 18:00 and also be unsuccessful.
- The value `0` is used directly because the `success` field stores Boolean values as numbers.

**Result:** I found 19 failed login attempts that happened after business hours.

---

### Task 2: Find Login Attempts on Specific Dates

The team was investigating an incident that occurred over two days: May 8 and May 9, 2022.

**SQL Query:**

```sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-08'
   OR login_date = '2022-05-09';
```

**What I learned:**

- `OR` allows me to match either of the given conditions.
- This is useful when an investigation covers more than one specific date.
- Both dates are included in the results.

**Result:** I retrieved 75 login attempts from the two dates.

---

### Task 3: Find Login Attempts from Outside Mexico

The investigation also required me to find login attempts that came from countries other than Mexico.

The database could contain country values such as `MEX` and `MEXICO`, so I used the `LIKE` operator with the `%` wildcard.

**SQL Query:**

```sql
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
```

**What I learned:**

- `LIKE 'MEX%'` matches values that begin with `MEX`.
- The `%` wildcard represents any characters that can come after `MEX`.
- Adding `NOT` reverses the condition, so records beginning with `MEX` are excluded.

**Result:** I found 144 login attempts that originated outside Mexico.

---

### Task 4: Find Marketing Employees in the East Building

The team needed a list of Marketing employees who worked in offices located in the East building so their workstations could be updated.

**SQL Query:**

```sql
SELECT *
FROM employees
WHERE department = 'Marketing'
  AND office LIKE 'East%';
```

**What I learned:**

- `AND` makes sure both conditions are satisfied.
- The employee must belong to the Marketing department.
- `LIKE 'East%'` matches office names that start with `East`, such as `East-170` or `East-320`.

**Result:** The query identified the employees who matched both requirements. The first matching record returned was for user `elarson`.

---

### Task 5: Find Employees in Finance or Sales

Another workstation update was needed for employees working in either the Finance or Sales department.

**SQL Query:**

```sql
SELECT *
FROM employees
WHERE department = 'Finance'
   OR department = 'Sales';
```

**What I learned:**

- `OR` lets me search for multiple possible values.
- When using `OR` for the same column, I need to write the column name in each condition.
- This query returns employees from both Finance and Sales.

**Result:** The first employee listed in the results was `lrodri`, from Sales.

---

### Task 6: Find Employees Who Are Not in IT

The IT department had already received the workstation update, so I needed to find everyone who was outside the Information Technology department.

**SQL Query:**

```sql
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';
```

**What I learned:**

- `NOT` reverses a condition.
- Here, it returns employees whose department is anything other than Information Technology.
- This made it easy to identify the employees who still needed the update.

**Result:** I retrieved 161 employee records that needed the software update.

---

## Conclusion

This activity helped me understand how `AND`, `OR`, and `NOT` can be used to build more detailed SQL queries.

I also practiced combining these operators with `LIKE` and the `%` wildcard to make searches more flexible. These techniques are especially useful in security work because analysts often need to narrow down large amounts of data and focus on records that match specific conditions.
