# LeetCode 1193 – Monthly Transactions I

**Difficulty:** Medium  
**Topic:** SQL, Aggregation, Group By  

---

## 📘 Problem Statement

Table: `Transactions`


+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| id             | int     |
| country        | varchar |
| state          | varchar |
| amount         | int     |
| trans_date     | date    |
+----------------+---------+

Each row contains information about a transaction.

Write an SQL query to find for each **month** and **country**:

- Total number of transactions
- Total amount of transactions
- Total number of approved transactions
- Total amount of approved transactions

Return the result table ordered by `month` and `country`.

---

## 🧪 Example

### Input

Transactions table:
+----+---------+----------+--------+------------+
| id | country | state    | amount | trans_date |
+----+---------+----------+--------+------------+
| 1  | US      | approved | 1000   | 2018-12-18 |
| 2  | US      | declined | 2000   | 2018-12-19 |
| 3  | US      | approved | 3000   | 2019-01-01 |
| 4  | FR      | approved | 1500   | 2019-01-02 |
+----+---------+----------+--------+------------+


### Output

+---------+---------+----------------+------------------+----------------------+------------------------+
| month   | country | trans_count    | trans_total_amt  | approved_count       | approved_total_amt     |
+---------+---------+----------------+------------------+----------------------+------------------------+
| 2018-12 | US      | 2              | 3000             | 1                    | 1000                   |
| 2019-01 | FR      | 1              | 1500             | 1                    | 1500                   |
| 2019-01 | US      | 1              | 3000             | 1                    | 3000                   |
+---------+---------+----------------+------------------+----------------------+------------------------+

## 💡 Key Insight

- Extract **month** from `trans_date`
- Use `GROUP BY month, country`
- Use conditional aggregation with `CASE WHEN`
- Count and sum approved transactions separately

---

## 🧠 Approach

1. Extract month using `DATE_FORMAT`
2. Group records by month and country
3. Use `COUNT(*)` for total transactions
4. Use `SUM(amount)` for total transaction amount
5. Use `CASE WHEN state = 'approved'` for approved metrics

---

## 🧾 Algorithm

1. Select month from `trans_date`
2. Group by month and country
3. Calculate:
   - Total transaction count
   - Total transaction amount
   - Approved transaction count
   - Approved transaction amount
4. Order by month and country

---

## ⏱️ Complexity Analysis

- **Time Complexity:** `O(n)`
- **Space Complexity:** `O(1)`
