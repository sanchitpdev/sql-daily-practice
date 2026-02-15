# 1321. Restaurant Growth

**Difficulty:** Medium  
**Topics:** SQL, Window Functions, Aggregation

---

## 🧾 Problem Statement
You are given a table **Customer**:

| Column Name | Type |
|------------|------|
| customer_id | int |
| name | varchar |
| visited_on | date |
| amount | int |

The restaurant wants to calculate the **7-day moving average** of total revenue.

Write an SQL query to:
- Compute the total amount of money earned **in the last 7 days (including current day)**.
- Calculate the **average daily revenue** for those 7 days.
- Only include days where a full 7-day window exists.

Return the result table ordered by `visited_on`.

---

## 📌 Example

### Input
```

Customer table:

+-------------+---------+------------+--------+
| customer_id | name    | visited_on | amount |
+-------------+---------+------------+--------+
| 1           | Jhon    | 2019-01-01 | 100    |
| 2           | Daniel  | 2019-01-02 | 110    |
| 3           | Jade    | 2019-01-03 | 120    |
...

```

### Output
```

+------------+--------+----------------+
| visited_on | amount | average_amount |
+------------+--------+----------------+
| 2019-01-07 | ...    | ...            |

```

---

## 🔑 Key Insight
- Multiple customers may visit on the same day → first **group by date**.
- Use a **7-day sliding window** with window functions:
```

ROWS BETWEEN 6 PRECEDING AND CURRENT ROW

````
- Ignore first 6 rows because they don’t have a full window.

---

## 🚀 Approach
1. Aggregate daily revenue using `GROUP BY visited_on`.
2. Apply window functions:
   - `SUM()` for total 7-day revenue.
   - `AVG()` for moving average.
3. Use `ROW_NUMBER()` to remove the first 6 days.
4. Order result by date.

---

## 🧠 Algorithm
1. Create a subquery to sum amount per day.
2. Apply window functions ordered by `visited_on`.
3. Assign row numbers.
4. Filter rows where `row_number >= 7`.
5. Return required columns.

---

## ⏱ Complexity
- **Time Complexity:** `O(n log n)` (sorting by date for window function)
- **Space Complexity:** `O(n)` (window processing)

---

