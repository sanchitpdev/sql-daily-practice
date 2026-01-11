# LeetCode 1934 – Confirmation Rate

**Difficulty:** Easy  
**Topic:** SQL, JOIN, Aggregation  

---

## Problem Statement
You are given two tables: `Signups` and `Confirmations`.

Table: `Signups`

| Column Name | Type |
|------------|------|
| user_id | int |
| time_stamp | datetime |

`user_id` is the primary key for this table.  
Each row indicates that a user signed up at a certain time.

---

Table: `Confirmations`

| Column Name | Type |
|------------|------|
| user_id | int |
| time_stamp | datetime |
| action | ENUM('confirmed', 'timeout') |

This table may contain multiple rows per user.  
Each row represents a confirmation request and its result.

Write an SQL query to calculate the **confirmation rate** for each user, defined as:

confirmation_rate = (number of 'confirmed' actions) / (total number of confirmation requests)

If a user has no confirmation records, the confirmation rate should be `0.00`.  
Round the result to **2 decimal places**.

---

## Example

### Input
**Signups table:**

| user_id | time_stamp |
|--------:|------------|
| 1 | 2020-01-01 |
| 2 | 2020-01-02 |
| 3 | 2020-01-03 |

**Confirmations table:**

| user_id | time_stamp | action |
|--------:|------------|--------|
| 1 | 2020-01-01 | confirmed |
| 1 | 2020-01-02 | timeout |
| 2 | 2020-01-03 | timeout |

### Output
| user_id | confirmation_rate |
|--------:|------------------|
| 1 | 0.50 |
| 2 | 0.00 |
| 3 | 0.00 |

---

## Approach
- Start from the `Signups` table to ensure all users are included
- Use a `LEFT JOIN` with `Confirmations`
- Count confirmed actions and total attempts
- Divide confirmed count by total count
- Handle users with no confirmations and round the result

---

## Complexity
- **Time Complexity:** `O(n)`
- **Space Complexity:** `O(1)`

---

## Code
See `solution.sql`

---

## Handwritten Notes
![Notes](notes.jpg)

