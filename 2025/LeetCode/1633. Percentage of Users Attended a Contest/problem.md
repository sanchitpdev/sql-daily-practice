# LeetCode 1633 – Percentage of Users Attended a Contest

## Difficulty
Easy

## Topic
SQL, Aggregation, Subquery

## Problem Statement
You are given two tables: `Users` and `Register`.

**Table: Users**

| Column Name | Type |
|------------|------|
| user_id    | int  |
| user_name  | varchar |

`user_id` is the primary key for this table.

**Table: Register**

| Column Name | Type |
|------------|------|
| contest_id | int  |
| user_id    | int  |

`(contest_id, user_id)` is the primary key for this table.

Write an SQL query to find the **percentage of users** who registered in each contest, rounded to **2 decimal places**.

Return the result table ordered by:
1. `percentage` in **descending** order
2. `contest_id` in **ascending** order

## Example

### Input
**Users table**

| user_id | user_name |
|--------|-----------|
| 6 | Alice |
| 2 | Bob |
| 7 | Alex |

**Register table**

| contest_id | user_id |
|-----------|---------|
| 215 | 6 |
| 209 | 2 |
| 208 | 2 |
| 210 | 6 |
| 208 | 6 |
| 209 | 7 |
| 209 | 6 |
| 215 | 7 |
| 208 | 7 |
| 210 | 2 |
| 210 | 7 |

### Output

| contest_id | percentage |
|-----------|------------|
| 208 | 100.00 |
| 209 | 100.00 |
| 210 | 100.00 |
| 215 | 66.67 |

## Key Insight
- Total users is fixed → derived from the `Users` table
- For each contest, count **distinct users**
- Percentage formula:

(contest_users / total_users) * 100

## Approach
1. Group records by `contest_id`
2. Count distinct `user_id` per contest
3. Divide by total number of users
4. Multiply by 100 and round to 2 decimal places
5. Sort according to the problem statement

## Algorithm
1. Select `contest_id`
2. Calculate percentage using `COUNT(DISTINCT user_id)`
3. Use a subquery to get total users
4. Apply `ROUND`
5. Order results

## Complexity Analysis

* **Time Complexity:** O(n)
* **Space Complexity:** O(1)

## Handwritten Notes
notes.jpg
