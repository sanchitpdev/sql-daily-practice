# 1070. Product Sales Analysis III

Difficulty: Medium  
Topic: SQL, Group By, Join  

---

## Problem Statement

Table: `Sales`

```txt
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| sale_id     | int     |
| product_id  | int     |
| year        | int     |
| quantity    | int     |
| price       | int     |
+-------------+---------+
````

(sale_id) is the primary key for this table.
Each row shows a sale of a product in a given year.

---

Write a SQL query to report, for each `product_id`, the **first year** it was sold, along with:

* `quantity`
* `price`

Return the result table in any order.

---

## Examples

Example 1:

Input:

Sales table:

```
+---------+------------+------+----------+-------+
| sale_id | product_id | year | quantity | price |
+---------+------------+------+----------+-------+
| 1       | 100        | 2008 | 10       | 5000  |
| 2       | 100        | 2009 | 12       | 5000  |
| 7       | 200        | 2011 | 15       | 9000  |
+---------+------------+------+----------+-------+
```

Output:

```
+------------+------------+----------+-------+
| product_id | first_year | quantity | price |
+------------+------------+----------+-------+
| 100        | 2008       | 10       | 5000  |
| 200        | 2011       | 15       | 9000  |
+------------+------------+----------+-------+
```

Explanation:

* Product 100 was first sold in 2008.
* Product 200 was first sold in 2011.

---

## Key Insight

We need the first year each product was sold.

Steps:

* Find the minimum year for each `product_id`
* Join it back with the Sales table
* Extract the quantity and price for that first year row

---

## Approach

1. Use `MIN(year)` grouped by `product_id` to get the first year.
2. Join this result with the original Sales table.
3. Select product_id, first_year, quantity, price.

---

## Complexity

Time Complexity:

O(n)

Space Complexity:

O(n)
