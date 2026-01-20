# LeetCode 550: Game Play Analysis IV

**Difficulty:** Medium  
**Topic:** SQL, Database, Aggregation

---

## 📘 Problem Statement

Table: **Activity**
```
| Column Name   | Type |
|--------------|------|
| player_id    | int  |
| device_id    | int  |
| event_date   | date |
| games_played | int  |
```
`(player_id, event_date)` is the primary key.

Each row shows the activity of a player on a given day.

---

### 🎯 Goal

Write an SQL query to report the **fraction of players** who logged in **again on the day after** the day they first logged in.

- Round the result to **2 decimal places**
- If no such players exist, return `0.00`

---

## 🧪 Example

### Input

**Activity table**
```
| player_id | device_id | event_date | games_played |
|----------|-----------|------------|--------------|
| 1        | 2         | 2016-03-01 | 5            |
| 1        | 2         | 2016-03-02 | 6            |
| 2        | 3         | 2017-06-25 | 1            |
| 3        | 1         | 2016-03-01 | 0            |
| 3        | 4         | 2016-03-02 | 2            |
```
### Output
```
| fraction |
|---------|
| 0.67    |
```
---

## 💡 Key Insight

1. First, find each player's **first login date**
2. Check whether the player logged in **exactly one day after** that date
3. Count such players
4. Divide by total number of distinct players
5. Round to 2 decimal places

---

## 🧠 Approach

- Use a **subquery** to compute the first login date per player
- Join it back with the Activity table
- Check `event_date = first_login_date + 1`
- Count distinct players satisfying this condition
- Divide by total players

---

## 🧾 Algorithm

1. Compute `MIN(event_date)` for each `player_id`
2. Join this result with the original table
3. Filter rows where `event_date = first_login_date + INTERVAL 1 DAY`
4. Count distinct `player_id`
5. Divide by total distinct players
6. Round the result to 2 decimal places

---

## ⏱️ Complexity Analysis

- **Time Complexity:** O(n)
- **Space Complexity:** O(n)

