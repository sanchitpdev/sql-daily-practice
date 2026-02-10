# 1978. Employees Whose Manager Left the Company

**Difficulty:** Easy  
**Topic:** SQL, Self Join

---

## Problem Statement
You are given an `Employees` table containing employee details including their
manager and salary.

Find the `employee_id` of employees who:
- Have a manager (`manager_id` is NOT NULL)
- Their manager is NOT present in the Employees table
- Their salary is less than 30000

Return the result ordered by `employee_id`.

---

## Examples

### Example 1
**Input:**  

Employees  
| employee_id | name    | manager_id | salary |
|-------------|---------|------------|--------|
| 1 | Boss    | NULL | 50000 |
| 2 | Alice   | 1    | 20000 |
| 3 | Bob     | 1    | 40000 |
| 4 | Charlie | 2    | 25000 |

**Output:**  

| employee_id |
|-------------|
| 4 |

**Explanation:**  
Employee 4 has a manager (2), but employee 2 is not present as a manager
anymore, and salary is below 30000.

---

## Key Insight
If a manager left the company, their record will be missing.
A self `LEFT JOIN` helps identify employees whose manager does not exist.

---

## Approach
- Perform a self `LEFT JOIN` on Employees table.
- If manager record is missing, joined columns will be NULL.
- Filter employees with salary < 30000 and valid manager_id.

---

## Algorithm
1. Left join Employees table with itself on manager_id.
2. Keep rows where manager is NULL.
3. Ensure employee has a manager and salary < 30000.
4. Order result by employee_id.

---

## Complexity
- **Time Complexity:** O(n)
- **Space Complexity:** O(1)

