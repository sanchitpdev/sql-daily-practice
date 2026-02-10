# 1164. Product Price at a Given Date

**Difficulty:** Medium  
**Topic:** SQL, Aggregation, Subquery

---

## Problem Statement

Table: `Products`

| Column Name   | Type |
|--------------|------|
| product_id   | int  |
| new_price    | int  |
| change_date  | date |

- `(product_id, change_date)` is the **primary key**.
- Each row indicates that the price of a product was changed to `new_price` on `change_date`.

**Task:**  
Find the **price of each product on `2019-08-16`**.

Rules:
- If the product has a price change **on or before** `2019-08-16`, use the **latest** such price.
- If the product has **no price change before** that date, its price is **10**.

---

## Example

### Input

| product_id | new_price | change_date |
|-----------|-----------|-------------|
| 1         | 20        | 2019-08-14  |
| 2         | 50        | 2019-08-14  |
| 1         | 30        | 2019-08-15  |
| 1         | 35        | 2019-08-16  |
| 2         | 65        | 2019-08-17  |

### Output

| product_id | price |
|-----------|-------|
| 1         | 35    |
| 2         | 50    |

---

## Key Insight

- For each product, we only care about price changes **up to `2019-08-16`**.
- Among those, we must pick the **most recent change date**.
- Products with **no valid record** default to price **10**.

---

## Approach

1. Filter rows where `change_date <= '2019-08-16'`.
2. For each `product_id`, get the **maximum change_date**.
3. Join back to fetch the corresponding `new_price`.
4. Use `LEFT JOIN` and `IFNULL` to handle default price `10`.

---

## Algorithm

1. Create a subquery to find the latest valid `change_date` per product.
2. Join it with the original table on `product_id` and `change_date`.
3. Replace missing prices with `10`.

---

