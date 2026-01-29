# LeetCode 1378 – Replace Employee ID With The Unique Identifier

**Difficulty:** Easy  
**Topic:** SQL, JOIN  

---

## Problem Statement
You are given two tables: `Employees` and `EmployeeUNI`.

The `Employees` table contains employee names and their IDs.  
The `EmployeeUNI` table contains the unique identifiers corresponding to some employee IDs.

Write an SQL query to show the **unique identifier** of each employee.  
If an employee does not have a unique identifier, return `NULL`.

---

## Example
### Employees
| id | name  |
|----|-------|
| 1  | Alice |
| 7  | Bob   |
| 11 | Meir  |
| 90 | Winston |
| 3  | Jonathan |

### EmployeeUNI
| id | unique_id |
|----|-----------|
| 3  | 1         |
| 11 | 7         |
| 90 | 11        |

---

## Key Insight
- Every employee must appear in the output
- Unique identifiers are **optional**
- A `LEFT JOIN` ensures all employees are included, even if they do not have a matching unique ID

---

## Approach (LEFT JOIN)
1. Use `Employees` as the base table
2. Perform a `LEFT JOIN` with `EmployeeUNI` on the `id` column
3. Select `unique_id` from `EmployeeUNI` and `name` from `Employees`

---

## Algorithm
1. Select `unique_id` and `name`
2. Join `Employees` with `EmployeeUNI` using `LEFT JOIN`
3. Match records using `Employees.id = EmployeeUNI.id`
4. Return the result set

---

## Complexity
- **Time Complexity:** `O(n)`
- **Space Complexity:** `O(1)`

---

## Code
See `solution.sql`

---

## Handwritten Notes
![Notes](notes.jpg)

