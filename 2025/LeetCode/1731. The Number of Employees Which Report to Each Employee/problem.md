# LeetCode 1731 — The Number of Employees Which Report to Each Employee

**Difficulty:** Easy  
**Topic:** SQL, Self Join, Aggregation  

---

## Problem Statement

You are given a table `Employees`:

- `employee_id` (unique ID)
- `name`
- `reports_to` (manager ID)
- `age`

Write an SQL query to report for each employee who has direct reports:

- `employee_id`
- `name`
- `reports_count` → number of employees reporting directly to them
- `average_age` → average age of direct reports rounded to the nearest integer

Return the result ordered by `employee_id`.

---

## Examples

### Example 1
```
**Input**

Employees table:

| employee_id | name  | reports_to | age |
|------------|-------|------------|-----|
| 9          | Herb  | null       | 43  |
| 6          | Alice | 9          | 41  |
| 4          | Bob   | 9          | 36  |
| 2          | Winston | null     | 37  |

**Output**

| employee_id | name | reports_count | average_age |
|------------|------|--------------|------------|
| 9          | Herb | 2            | 39         |
```
---

## Key Insight

Since both managers and employees are stored in the same table:

- We use a **self join**
- Managers are those who appear in `reports_to`

We calculate:

- Total number of direct reports using `COUNT()`
- Average age of reports using `AVG()` and `ROUND()`

---

## Approach

- Take `e1` as manager
- Take `e2` as employee who reports to manager
- Join where:

  `e2.reports_to = e1.employee_id`

- Group by manager
- Compute required aggregates

---

## Algorithm

1. Perform self join on Employees
2. Group by manager employee_id and name
3. Count direct reports
4. Compute rounded average age
5. Order result by employee_id

---

## Complexity

- **Time Complexity:** O(N)
- **Space Complexity:** O(1)
