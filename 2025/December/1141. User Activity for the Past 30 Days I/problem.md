# LeetCode 1141 – User Activity for the Past 30 Days I

## Difficulty
Easy

## Topic
SQL, Aggregation, Date Filtering

---

## Problem Statement
```
Table: Activity

| Column Name     | Type    |
|----------------|---------|
| user_id        | int     |
| session_id     | int     |
| activity_date  | date    |
| activity_type  | enum    |
```
Each row represents an activity performed by a user on a specific date.

Write an SQL query to find the daily active user count for the 30-day period ending on **2019-07-27** (inclusive).

A user is considered active on a day if they performed at least one activity on that day.

Return the result table in any order.

---

## Examples

### Example 1

**Input:**
```
Activity table:

| user_id | session_id | activity_date | activity_type |
|--------|------------|--------------|--------------|
| 1      | 1          | 2019-07-20   | open_session |
| 1      | 1          | 2019-07-20   | scroll_down  |
| 2      | 2          | 2019-07-21   | open_session |
| 2      | 2          | 2019-07-21   | scroll_down  |
| 3      | 3          | 2019-07-22   | open_session |

**Output:**

| day        | active_users |
|-----------|--------------|
| 2019-07-20 | 1 |
| 2019-07-21 | 1 |
| 2019-07-22 | 1 |
```
---

## Key Insight

- A user can perform multiple activities on the same day.
- But we should count each user only once per day.
- Therefore, we use:

COUNT(DISTINCT user_id)

We also filter only the last 30 days:

2019-06-28 to 2019-07-27

---

## Approach

1. Filter records between the required date range.
2. Group activities by date.
3. Count distinct users for each day.
4. Output as day + active user count.

---

## Algorithm

1. Select activity_date as day
2. Apply WHERE clause for date range
3. GROUP BY activity_date
4. COUNT distinct user_id per day

---

## Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)
