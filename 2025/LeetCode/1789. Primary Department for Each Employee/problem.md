# LeetCode 1789 — Primary Department for Each Employee

**Difficulty:** Easy  
**Topic:** SQL, Database  

---

## Problem Statement

Table: **Employee**

| Column Name     | Type    |
|----------------|---------|
| employee_id     | int     |
| department_id   | int     |
| primary_flag    | varchar |

- `(employee_id, department_id)` is the primary key.
- `primary_flag` is either `'Y'` or `'N'`.
- Each employee can belong to multiple departments.
- If an employee belongs to multiple departments, one of them will be marked as primary (`'Y'`).

---

## Task

Write an SQL query to report the **primary department** for each employee.

- If an employee has a department marked `'Y'`, return that one.
- If the employee belongs to only one department, return it even if marked `'N'`.

Return the result table in any order.

---

## Example

### Input

Employee table:

| employee_id | department_id | primary_flag |
|------------|--------------|--------------|
| 1          | 1            | N            |
| 2          | 1            | Y            |
| 2          | 2            | N            |
| 3          | 3            | N            |

### Output

| employee_id | department_id |
|------------|--------------|
| 1          | 1            |
| 2          | 1            |
| 3          | 3            |

---

## Key Insight

- Employees with a primary department have `primary_flag = 'Y'`.
- Employees without any `'Y'` must have only one department, so we return that department.

---

## Approach

1. Select all employees whose `primary_flag = 'Y'`.
2. Select employees who do **not** have any `'Y'` flag.
3. Combine both results using `UNION`.

---
