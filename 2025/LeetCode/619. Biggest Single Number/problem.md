# 619. Biggest Single Number

**Difficulty:** Easy  
**Topic:** SQL / Aggregation  

---

## Problem Statement

You are given a table:

### MyNumbers

| Column Name | Type |
|------------|------|
| num        | int  |

Each row contains an integer.

A **single number** is a number that appears **only once** in the table.

Write an SQL query to report the **largest single number**.  
If there is no single number, report `null`.

---

## Example

### Input

MyNumbers table:

| num |
|-----|
| 8   |
| 8   |
| 3   |
| 3   |
| 1   |
| 4   |
| 5   |
| 6   |

### Output

| num |
|-----|
| 6   |

Explanation:  
Single numbers are `1, 4, 5, 6` and the biggest is `6`.

---

## Key Insight

- First, identify numbers that appear exactly once.
- Then, select the maximum among them.
- If no such number exists, return `null`.

---

## Approach

- Group by `num`
- Filter groups with `COUNT(*) = 1`
- Select the maximum number

---

## Algorithm

1. Group all numbers by `num`
2. Keep only those appearing once
3. Take the largest using `MAX()`

---

## Complexity

- **Time Complexity:** O(n)  
- **Space Complexity:** O(1)  

---
