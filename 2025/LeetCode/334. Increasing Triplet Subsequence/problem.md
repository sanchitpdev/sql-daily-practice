# 🚀 LeetCode 185 — Department Top Three Salaries

**Difficulty:** Hard  
**Topics:** SQL, Window Functions, Ranking

---

# 🧩 Problem Statement

Table: `Employee`

| Column Name | Type    |
|------------|---------|
| id         | int     |
| name       | varchar |
| salary     | int     |
| departmentId | int  |

Table: `Department`

| Column Name | Type    |
|------------|---------|
| id         | int     |
| name       | varchar |

Write a SQL query to find employees who are among the **top three highest salaries** in each department.

Return the result table in any order.

---

# 🧪 Examples

### Example

**Employee**

```

+----+-------+--------+--------------+
| id | name  | salary | departmentId |
+----+-------+--------+--------------+
| 1  | Joe   | 85000  | 1            |
| 2  | Henry | 80000  | 2            |
| 3  | Sam   | 60000  | 2            |
| 4  | Max   | 90000  | 1            |
| 5  | Janet | 69000  | 1            |
| 6  | Randy | 85000  | 1            |
| 7  | Will  | 70000  | 1            |
+----+-------+--------+--------------+

```

**Department**

```

+----+----------+
| id | name     |
+----+----------+
| 1  | IT       |
| 2  | Sales    |
+----+----------+

```

**Output**

```

+------------+----------+--------+
| Department | Employee | Salary |
+------------+----------+--------+
| IT         | Max      | 90000  |
| IT         | Joe      | 85000  |
| IT         | Randy    | 85000  |
| IT         | Will     | 70000  |
| Sales      | Henry    | 80000  |
| Sales      | Sam      | 60000  |
+------------+----------+--------+

```

---

# 🔑 Key Insight

We need **Top 3 salaries per department**, not overall.

Important observations:

- Ranking must restart for each department.
- Duplicate salaries must be handled.
- Window function `DENSE_RANK()` is ideal because:
  - Same salary → same rank.
  - No gaps in ranking.

---

# 🧠 Approach

1. Join `Employee` with `Department`.
2. Use a window function:


DENSE_RANK() OVER (PARTITION BY department ORDER BY salary DESC)


3. Assign rank inside each department.
4. Filter only rows where rank ≤ 3.

Why `DENSE_RANK()`?

Salary: 90000, 85000, 85000, 70000
Ranks : 1,     2,     2,     3


All valid top three salaries remain included.

---

# ⚙️ Algorithm

Join Employee and Department tables

Compute:
rank = DENSE_RANK() partitioned by department
ordered by salary descending

Filter:
rank <= 3

Select department name, employee name, salary

---

# ⏱️ Complexity Analysis

- **Time Complexity:** Depends on sorting per department  
  ≈ `O(n log n)`
- **Space Complexity:** `O(n)` for ranking operation.

---

