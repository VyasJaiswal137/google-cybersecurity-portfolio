# Activity: Join Tables in SQL

## Activity Overview
In this lab activity, I acted as a security analyst investigating a security incident involving compromised machines. Because necessary security details were split across multiple database tables, I used SQL join operations (`INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`) to combine datasets using shared linking columns. This enabled me to correlate user identities, device specs, and login attempts across the organization's database.

---

## Scenario
To conduct a thorough incident investigation, the security team required precise reporting on hardware assignments, unassigned assets, users lacking hardware, and employee login histories. I queried the `machines`, `employees`, and `log_in_attempts` tables to bridge data gaps and generate consolidated views for analysis.

---

## Tasks & SQL Solutions

### Task 1: Match Employees to Their Machines
To identify which employees are using which machines, I joined the `machines` table (hardware specs) and the `employees` table (user identities). Both tables share a common linking key: `device_id`. Using dot notation (`table.column`) prevented column name ambiguity.

**SQL Query:**
```sql
SELECT * 
FROM machines 
INNER JOIN employees 
  ON machines.device_id = employees.device_id;