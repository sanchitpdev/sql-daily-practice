# 585. Investments in 2016

## 🟢 Difficulty
Medium

## 🧭 Topic
SQL, Aggregation, Filtering, Self-Condition, Group By

---

## 📘 Problem Statement
Table: `Insurance`

| Column Name | Type  |
|-------------|-------|
| pid         | int   |
| tiv_2015    | float |
| tiv_2016    | float |
| lat         | float |
| lon         | float |

`pid` is the primary key.

Write a SQL query to report the **sum of all tiv_2016** where:

1. The policyholder has the **same tiv_2015 value** as at least one other policyholder.
2. The **(lat, lon)** location pair is **unique** (no other record has the same latitude and longitude).

Return the result rounded to **two decimal places**.

---

## 🧪 Example

### Input
Insurance table:

| pid | tiv_2015 | tiv_2016 | lat | lon |
|-----|----------|----------|-----|-----|
| 1   | 10       | 5        | 10  | 10  |
| 2   | 20       | 20       | 20  | 20  |
| 3   | 10       | 30       | 20  | 20  |
| 4   | 10       | 40       | 40  | 40  |

### Output
45.00

---

## 🔑 Key Insight
We must filter rows using **two conditions**:

- `tiv_2015` must appear more than once → use `GROUP BY tiv_2015 HAVING COUNT(*) > 1`.
- `(lat, lon)` must be unique → group by both and keep only `COUNT(*) = 1`.

After filtering valid records, compute:

SUM(tiv_2016)

---

## 🚀 Approach
- First identify duplicated `tiv_2015` values.
- Then identify unique `(lat, lon)` locations.
- Select only rows satisfying both conditions.
- Aggregate the `tiv_2016` values and round the result.

---

## 🧩 Algorithm
1. Find all tiv_2015 values that appear more than once.
2. Find all (lat, lon) pairs that appear exactly once.
3. Filter original table using these two conditions.
4. Compute `ROUND(SUM(tiv_2016), 2)`.

---

## ⏱️ Complexity

**Time Complexity:**  
O(n log n) (due to grouping and aggregation operations)

**Space Complexity:**  
O(n) (temporary grouping results)

