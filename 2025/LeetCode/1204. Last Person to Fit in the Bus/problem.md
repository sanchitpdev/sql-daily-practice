# 1204. Last Person to Fit in the Bus

**Difficulty:** Medium  
**Topic:** SQL, Window Functions

---

## Problem Statement

Table: `Queue`

| Column Name  | Type    |
|-------------|---------|
| person_id   | int     |
| person_name | varchar |
| weight      | int     |
| turn        | int     |

- `turn` determines the order in which people get on the bus.
- The bus has a **maximum weight capacity of 1000**.
- People board the bus one by one in increasing order of `turn`.

**Task:**  
Return the **name of the last person** who can get on the bus **without exceeding** the weight limit.

---

## Example

### Input

| person_id | person_name | weight | turn |
|----------|-------------|--------|------|
| 5        | Alice       | 250    | 1    |
| 4        | Bob         | 175    | 2    |
| 3        | Alex        | 350    | 3    |
| 6        | John Cena   | 400    | 4    |
| 1        | Winston     | 500    | 5    |
| 2        | Marie       | 200    | 6    |

### Output

| person_name |
|-------------|
| John Cena   |

---

## Key Insight

- We must process people **in order of `turn`**.
- Track a **running total** of weights.
- The answer is the **last person whose cumulative weight ≤ 1000**.

---

## Approach

1. Use a **window function** to compute cumulative weight.
2. Filter rows where cumulative weight is within the limit.
3. Pick the person with the **maximum cumulative weight** that does not exceed 1000.

---

## Algorithm

1. Calculate cumulative weight using `SUM(weight) OVER (ORDER BY turn)`
2. Keep only rows where cumulative weight ≤ 1000
3. Sort by cumulative weight descending
4. Return the top result

---

