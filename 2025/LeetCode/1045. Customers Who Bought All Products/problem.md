# LeetCode 1045 - Customers Who Bought All Products

---

## Difficulty
Easy  

---

## Topic
SQL, GROUP BY, HAVING, Subquery  

---

## Problem Statement
You are given two tables:

### Customer
- customer_id: ID of the customer  
- product_key: product bought by the customer  

### Product
- product_key: all available products  

Write an SQL query to report the customer IDs of customers who have bought all the products listed in the Product table.

Return the result table in any order.

---

## Examples

### Example 1
```
Input:

Customer

| customer_id | product_key |
|------------|------------|
| 1          | 5          |
| 1          | 6          |
| 2          | 5          |
| 2          | 6          |
| 2          | 7          |

Product

| product_key |
|------------|
| 5          |
| 6          |

Output:

| customer_id |
|------------|
| 1          |
| 2          |
```
---

## Key Insight
A customer has bought all products if the number of distinct products they purchased is equal to the total number of products available.

So we compare:

- COUNT(DISTINCT product_key) per customer  
with  
- COUNT(*) of all products in Product table  

---

## Approach
1. Group rows by customer_id.
2. Count distinct products purchased by each customer.
3. Count total products in Product table.
4. Select customers whose counts match.

---

## Algorithm
- GROUP BY customer_id  
- HAVING COUNT(DISTINCT product_key) = (SELECT COUNT(*) FROM Product)

---

## Complexity
Time Complexity: O(n)  
Space Complexity: O(1)  

---

