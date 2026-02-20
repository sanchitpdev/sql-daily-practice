# 1667. Fix Names in a Table

**Difficulty:** Easy  
**Topic:** SQL, String Functions

---

## 🧾 Problem Statement

Table: `Users`

| Column Name | Type |
|---|---|
| user_id | int |
| name | varchar |

`user_id` is the primary key for this table.  
Each row contains the name of a user written in random casing.

Write an SQL query to fix the names so that:

- The **first character** is uppercase.
- The **remaining characters** are lowercase.

Return the result ordered by `user_id`.

---

## 📌 Example

### Input
```

Users table:
+---------+-------+
| user_id | name  |
+---------+-------+
| 1       | aLice |
| 2       | bOB   |
+---------+-------+

```

### Output
```

+---------+-------+
| user_id | name  |
+---------+-------+
| 1       | Alice |
| 2       | Bob   |
+---------+-------+
```
---

## 🔑 Key Insight

We need to normalize the casing of each name:

- First letter → `UPPER()`
- Remaining letters → `LOWER()`

This can be achieved by splitting the string:

first character + remaining substring

---

## 🧠 Approach

1. Extract the first character using `LEFT(name, 1)`.
2. Convert it to uppercase using `UPPER()`.
3. Extract the rest of the string using `SUBSTRING(name, 2)`.
4. Convert the remaining part to lowercase using `LOWER()`.
5. Combine both parts using `CONCAT()`.
6. Sort results by `user_id`.

---

## ⚙️ Algorithm

SELECT user_id,
CONCAT(
UPPER(LEFT(name,1)),
LOWER(SUBSTRING(name,2))
) AS name
FROM Users
ORDER BY user_id;

---

## ⏱️ Complexity Analysis

**Time Complexity:** `O(n)`  
- Each row is processed once.

**Space Complexity:** `O(1)`  
- No extra storage beyond output.

---

