# Employee Bonus

**Difficulty:** Easy  
**Topic:** SQL, JOIN  

---

## Problem Statement
Table: `Employee`

| Column Name | Type    |
|------------|---------|
| empId      | int     |
| name       | varchar |
| supervisor | int     |
| salary     | int     |

`empId` is the primary key for this table.

---

Table: `Bonus`

| Column Name | Type |
|------------|------|
| empId      | int  |
| bonus      | int  |

`empId` is the primary key for this table.

---

Write an SQL query to report the **name and bonus amount of each employee** whose bonus is **less than 1000**.

If an employee **does not have a bonus**, their bonus should be reported as **null**.

Return the result table in **any order**.

---

## Examples

### Input

**Employee table**

| empId | name  | supervisor | salary |
|-----|------|-----------|--------|
| 3   | Brad | null      | 4000   |
| 1   | John | 3         | 1000   |
| 2   | Dan  | 3         | 2000   |
| 4   | Thomas | 3       | 4000   |

**Bonus table**

| empId | bonus |
|-----|------|
| 2   | 500  |
| 4   | 2000 |

---

### Output

| name | bonus |
|------|-------|
| Brad | null  |
| John | null  |
| Dan  | 500   |

---

## Key Insight
Employees without a bonus record must still appear in the result.  
This requires keeping all rows from the `Employee` table and handling missing bonus values using `NULL`.

---

## Approach
- Keep all employees in the result set.
- Match bonuses when they exist.
- Filter employees whose bonus is either:
  - `NULL` (no bonus record), or
  - less than `1000`.

---

## Algorithm
1. Perform a `LEFT JOIN` from `Employee` to `Bonus` using `empId`.
2. Apply a condition to select rows where:
   - bonus is `NULL`, or
   - bonus < 1000.
3. Select only the employee name and bonus.

---

## Complexity
- **Time Complexity:** O(n)
- **Space Complexity:** O(1)

---

## Code Reference
SQL

---

## Handwritten Notes
![notes](notes.jpg)

