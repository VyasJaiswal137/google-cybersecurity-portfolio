# Activity: Apply More Filters in SQL

## Activity Overview

In this activity, I worked as a security analyst investigating login activity stored in an organization's database. I built on basic SQL queries by using different filters to narrow down the results.

The main goal was to find specific login records based on dates, date ranges, exact times, and unique login IDs. I used SQL comparison operators such as `>`, `=` and the `BETWEEN` operator to make the searches more precise.

---

## Scenario

While reviewing the security logs, the security operations team needed specific sets of login records to investigate recent activity and possible unusual events.

I worked with the `log_in_attempts` table and used SQL filters to find the records that matched different investigation requirements.

---

## Tasks & SQL Solutions

### Task 1: Find Login Attempts After a Certain Date

The security team wanted to investigate login activity that happened after January 15, 2023.

**SQL Query:**

```sql
SELECT *
FROM log_in_attempts
WHERE login_date > '2023-01-15';
```

**What I learned:**

- The `>` operator selects records that occurred after the specified date.
- The date is written in the `YYYY-MM-DD` format.
- This helped me focus on more recent login activity instead of looking through older records.

---

### Task 2: Find Login Attempts Within a Date Range

Next, I needed to review login activity from February 1, 2023, through February 7, 2023.

**SQL Query:**

```sql
SELECT *
FROM log_in_attempts
WHERE login_date BETWEEN '2023-02-01' AND '2023-02-07';
```

**What I learned:**

- The `BETWEEN` operator is useful when I need records within a specific range.
- `BETWEEN` is inclusive, so both February 1 and February 7 are included.
- Using a date range makes it easier to focus on activity that happened during a particular investigation period.

---

### Task 3: Find Login Attempts at an Exact Time

For another part of the investigation, I needed to find all login attempts that occurred exactly at 09:30:00 AM.

**SQL Query:**

```sql
SELECT *
FROM log_in_attempts
WHERE login_time = '09:30:00';
```

**What I learned:**

- The `=` operator is used when I want an exact match.
- The time is written in `HH:MM:SS` format.
- Searching for an exact time can be useful when comparing database records with other security logs.

---

### Task 4: Find a Login Attempt Using Its ID

Finally, I needed to investigate one specific login event with the `login_id` of `503`.

**SQL Query:**

```sql
SELECT *
FROM log_in_attempts
WHERE login_id = 503;
```

**What I learned:**

- The `=` operator can also be used to find an exact numeric value.
- Since `login_id` is a number, it does not need quotation marks.
- Searching by a unique ID makes it quick to locate a specific event in the logs.

---

## Conclusion

This activity helped me understand how SQL filters can make security log investigations more focused and efficient.

By using operators such as `>`, `=`, and `BETWEEN`, I was able to search for login attempts based on specific dates, date ranges, exact times, and unique IDs. These filtering techniques are useful when security analysts need to quickly narrow down large amounts of log data and investigate specific events.
