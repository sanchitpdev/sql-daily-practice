# 1729. Find Followers Count

**Difficulty:** Easy  
**Topic:** SQL / Aggregation  

---

## Problem Statement

You are given a table:

### Followers
```
| Column Name | Type |
|------------|------|
| user_id    | int  |
| follower_id| int  |
```
- `user_id` is the user being followed  
- `follower_id` is the user who follows  

Write an SQL query to find the number of followers for each `user_id`.

Return the result table ordered by `user_id` in ascending order.

---

## Example

### Input

Followers table:
```
| user_id | follower_id |
|--------|------------|
| 0      | 1          |
| 1      | 0          |
| 2      | 0          |
| 2      | 1          |
```
### Output
```
| user_id | followers_count |
|--------|-----------------|
| 0      | 1               |
| 1      | 1               |
| 2      | 2               |
```
---

## Key Insight

- Each row represents one follower relationship.
- To count followers per user, we group by `user_id`.
- Use `COUNT(follower_id)` to get number of followers.

---

## Approach

- Group records by `user_id`
- Count total followers for each user
- Sort result by `user_id`

---

## Algorithm

1. Select `user_id`
2. Count followers using `COUNT(follower_id)`
3. Group by `user_id`
4. Order by `user_id`

---

## Complexity

- **Time Complexity:** O(n)  
- **Space Complexity:** O(1)  

---
