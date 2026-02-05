# LeetCode 180 – Consecutive Numbers

**Difficulty:** Medium  
**Topic:** SQL, Joins

---

## Problem Statement

Table: `Logs`

| Column Name | Type |
|------------|------|
| id | int |
| num | int |

`id` is the primary key and increases continuously.

Write an SQL query to find all numbers that appear **at least three times consecutively**.

Return the result table in **any order**.

---

## Example

### Input
```

Logs
+----+-----+
| id | num |
+----+-----+
| 1  | 1   |
| 2  | 1   |
| 3  | 1   |
| 4  | 2   |
| 5  | 1   |
| 6  | 2   |
| 7  | 2   |
+----+-----+

```

### Output
```

+-----------------+
| ConsecutiveNums |
+-----------------+
| 1               |
+-----------------+

````

---

## Key Insight

If the same number appears in three rows with **consecutive ids**, then it satisfies the condition.

---

## Approach

Use self-joins on the `Logs` table to compare three consecutive rows.

---

## Complexity

* **Time Complexity:** O(n)
* **Space Complexity:** O(1)
