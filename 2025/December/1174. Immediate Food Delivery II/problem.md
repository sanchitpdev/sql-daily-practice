**Difficulty:** Medium  
**Topic:** SQL, Aggregation, Percentage Calculation  

---

## Problem Statement

Table: `Delivery`
```
| Column Name | Type |
|------------|------|
| delivery_id | int |
| customer_id | int |
| order_date | date |
| customer_pref_delivery_date | date |
```
Each row contains information about a food delivery order.

A customer is called **immediate** if their **first order’s order_date** is equal to their **customer_pref_delivery_date**.

Write an SQL query to find the **percentage of immediate orders among all customers**, rounded to **2 decimal places**.

---

## Example

### Input
```

Delivery table:
+-------------+-------------+------------+-----------------------------+
| delivery_id | customer_id | order_date | customer_pref_delivery_date |
+-------------+-------------+------------+-----------------------------+
| 1           | 1           | 2019-08-01 | 2019-08-02                  |
| 2           | 2           | 2019-08-02 | 2019-08-02                  |
| 3           | 1           | 2019-08-11 | 2019-08-11                  |
| 4           | 3           | 2019-08-24 | 2019-08-24                  |
+-------------+-------------+------------+-----------------------------+

```

### Output
```

+----------------------+
| immediate_percentage |
+----------------------+
| 66.67                |
+----------------------+

````

---

## Key Insight

- Only the **first order per customer** matters
- We must:
  1. Find each customer’s **earliest order_date**
  2. Check whether it equals `customer_pref_delivery_date`
  3. Compute percentage of such customers

---

## Approach

1. Use a subquery to get the **first order** of each customer
2. Count customers whose first order is **immediate**
3. Divide by total number of customers
4. Multiply by 100 and round to 2 decimals

---

## Algorithm

1. Group records by `customer_id`
2. Select minimum `order_date` per customer
3. Compare with `customer_pref_delivery_date`
4. Calculate percentage

