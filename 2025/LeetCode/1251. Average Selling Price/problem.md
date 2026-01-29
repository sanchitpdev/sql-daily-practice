# LeetCode 1251 – Average Selling Price

## Difficulty
Easy

## Topic
SQL, JOIN, Aggregation

## Problem Statement
You are given two tables: `Prices` and `UnitsSold`.

Table: `Prices`

| Column Name | Type |
|------------|------|
| product_id | int |
| start_date | date |
| end_date | date |
| price | int |

- `(product_id, start_date, end_date)` is the primary key.
- Each row indicates the price of a product during a time period.

Table: `UnitsSold`

| Column Name | Type |
|------------|------|
| product_id | int |
| purchase_date | date |
| units | int |

- There is no primary key for this table.
- Each row indicates the number of units sold of a product on a specific date.

Write an SQL query to find the **average selling price** for each product.  
The average selling price should be **rounded to 2 decimal places**.  
If a product has **no sales**, its average selling price should be **0**.

---

## Example

**Input**

Prices table:
| product_id | start_date | end_date | price |
|-----------|------------|----------|-------|
| 1 | 2019-02-17 | 2019-02-28 | 5 |
| 1 | 2019-03-01 | 2019-03-22 | 20 |
| 2 | 2019-02-01 | 2019-02-20 | 15 |

UnitsSold table:
| product_id | purchase_date | units |
|-----------|---------------|-------|
| 1 | 2019-02-25 | 100 |
| 1 | 2019-03-01 | 15 |
| 2 | 2019-02-10 | 200 |

**Output**

| product_id | average_price |
|-----------|---------------|
| 1 | 6.96 |
| 2 | 15.00 |

---

## Key Insight
- Average selling price is a **weighted average**
- Products with **no sales must still appear**
- Sales must match the **correct price date range**

---

## Approach
1. Use `LEFT JOIN` to keep all products from `Prices`
2. Match sales using `purchase_date BETWEEN start_date AND end_date`
3. Compute total revenue using `SUM(units * price)`
4. Divide by total units sold
5. Handle `NULL` using `IFNULL`
6. Round result to 2 decimal places

---

## Algorithm
1. Join `Prices` with `UnitsSold` using `LEFT JOIN`
2. Apply date range condition in `ON` clause
3. Group by `product_id`
4. Calculate weighted average price
5. Replace `NULL` with `0`

---

## SQL Query
solution.sql
---

## Complexity

* Time Complexity: `O(n)`
* Space Complexity: `O(1)`

---

## Handwritten Notes

notes.jpg
