# LeetCode 1211 – Queries Quality and Percentage

**Difficulty:** Easy  
**Topic:** SQL, Aggregation, CASE, GROUP BY

---

## 📘 Problem Statement

Table: `Queries`

| Column Name | Type    |
|------------|---------|
| query_name | varchar |
| result     | varchar |
| position   | int     |
| rating     | int     |

Each row represents a query result with its position and rating.

- **Query quality** is defined as:
  
AVG(rating / position)

- **Poor query percentage** is defined as the percentage of queries where:

rating < 3

Write an SQL query to report:
- `query_name`
- `quality`
- `poor_query_percentage`

Round both numeric values to **2 decimal places**.

---

## 🧪 Example

### Input

Queries table:
+------------+----------+----------+--------+
| query_name | result   | position | rating |
+------------+----------+----------+--------+
| Dog        | Golden   | 1        | 5      |
| Dog        | Husky    | 2        | 4      |
| Dog        | Poodle   | 3        | 1      |
| Cat        | Persian  | 1        | 5      |
| Cat        | Siamese  | 2        | 3      |
+------------+----------+----------+--------+

```

### Output

```

+------------+---------+-----------------------+
| query_name | quality | poor_query_percentage |
+------------+---------+-----------------------+
| Dog        | 2.11    | 33.33                 |
| Cat        | 2.75    | 0.00                  |
+------------+---------+-----------------------+

```

---

## 💡 Key Insight

- Use `AVG(rating / position)` to compute **quality**
- Use `CASE WHEN rating < 3 THEN 1 ELSE 0 END` to identify poor queries
- Percentage is calculated as:

```

(SUM(poor_queries) / COUNT(*)) * 100

````

- `ROUND(value, 2)` is required for final output formatting

---

## 🛠️ Approach

1. Group records by `query_name`
2. Calculate quality using `AVG(rating / position)`
3. Calculate poor query percentage using conditional aggregation
4. Round both values to two decimal places

---

## 🧩 Algorithm

1. Select `query_name`
2. Compute:
   - `ROUND(AVG(rating / position), 2)` as `quality`
   - `ROUND(SUM(CASE WHEN rating < 3 THEN 1 ELSE 0 END) * 100.0 / COUNT(*), 2)`
3. Group results by `query_name`

---

## ⏱️ Complexity Analysis

- **Time Complexity:** `O(n)`
- **Space Complexity:** `O(1)`

---

