# Activity: Joining Tables in SQL
 
## Overview
 
For this lab, I stepped into the role of a security analyst looking into a potential compromise. The problem was that the information I needed was scattered across several database tables, so I had to pull it together using SQL joins — `INNER JOIN`, `LEFT JOIN`, and `RIGHT JOIN` — to line up user identities, device details, and login history in one place.
 
---
 
## The Scenario
 
The security team needed clear answers to a few questions: who's using which machine, which machines aren't assigned to anyone, which employees don't have hardware at all, and what does everyone's login history look like. To get there, I worked across three tables — `machines`, `employees`, and `log_in_attempts` — joining them together to close the gaps and build a full picture.
 
---
 
## Task 1: Matching Employees to Their Machines
 
First step was figuring out who's using what. I joined `machines` (hardware info) with `employees` (user info) on the field they both share, `device_id`. I used table.column notation throughout so there was no confusion about which `device_id` I meant.
 
```sql
SELECT * 
FROM machines 
INNER JOIN employees 
  ON machines.device_id = employees.device_id;
```
 
**What I learned:** An `INNER JOIN` only keeps rows where both tables have a match — anything without a corresponding entry on the other side gets dropped. That made `machines.device_id` and `employees.device_id` the bridge tying hardware records to actual people.
 
**Result:** 185 rows came back, each pairing a machine with the employee it's assigned to.
 
---
 
## Task 2: Catching What Got Missed
 
An inner join is great for confirmed matches, but it hides anything that *doesn't* have a pair — which is exactly the stuff a security audit cares about. So I ran two more queries to surface unassigned machines and employees without hardware.
 
### Left Join — Finding Unassigned Machines
 
Using a `LEFT JOIN` keeps every row from `machines`, whether or not it has a matching employee.
 
```sql
SELECT * 
FROM machines 
LEFT JOIN employees 
  ON machines.device_id = employees.device_id;
```
 
**What I learned:** Any machine sitting unused shows up with `NULL` values in all the employee columns — that's the giveaway for unassigned inventory.
 
**Result:** The final row in the output had a `NULL` username, flagging a machine with no one attached to it.
 
### Right Join — Finding Employees Without a Device
 
Flip it around with a `RIGHT JOIN`, and now every row from `employees` is preserved, matched machine or not.
 
```sql
SELECT * 
FROM machines 
RIGHT JOIN employees 
  ON machines.device_id = employees.device_id;
```
 
**What I learned:** Employees who haven't been issued a laptop show up with `NULL` across every machine-related column.
 
**Result:** The last row belonged to user `areyes` — someone without an assigned device.
 
**A note on style:** In real-world security work, most analysts skip `RIGHT JOIN` altogether and just reorder the tables to use `LEFT JOIN` instead (e.g., `FROM employees LEFT JOIN machines`). It's easier to read left to right, and it matches how most log-analysis workflows are already structured.
 
---
 
## Task 3: Pulling Login History
 
Last piece was connecting people to their login activity. I joined `employees` and `log_in_attempts` on `username`, since that's the field both tables have in common.
 
```sql
SELECT * 
FROM employees 
INNER JOIN log_in_attempts 
  ON employees.username = log_in_attempts.username;
```
 
**What I learned:** Joining on `username` links each employee's profile straight to their authentication history. Prefixing both sides with the table name kept things unambiguous and avoided any conflicts.
 
**Result:** 200 login records came back, each one tied to a verified employee.
 
---
 
## Wrap-Up
 
This exercise was a solid, hands-on way to see how SQL joins solve a real problem: pulling apart data that lives in separate places and putting it back together in a way that actually answers a question. `INNER JOIN` was useful for confirming clean matches, while `LEFT JOIN` and `RIGHT JOIN` were what actually surfaced the gaps — unassigned machines, employees without hardware — which turned out to be the more interesting part of the investigation. Being able to move between assets, accounts, and login activity like this is a core skill for anything involving incident response or access auditing.
