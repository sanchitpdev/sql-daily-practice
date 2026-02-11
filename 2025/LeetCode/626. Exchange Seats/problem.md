# 626. Exchange Seats

- **Difficulty:** Medium  
- **Topic:** SQL, CASE, ORDER BY

---

## 🧾 Problem Statement
Table: `Seat`

| Column Name | Type |
|-------------|------|
| id | int |
| student | varchar |

- `id` is the primary key.
- Each row contains the name of a student and their seat id.
- Seat ids start from 1 and increase continuously.

Write a SQL query to **swap the seat id of every two consecutive students**.
- If the number of students is odd, the last student keeps their seat.

Return the result ordered by `id`.

---

## 📌 Examples

### Example
Input:

Seat table:
| id | student |
|----|---------|
| 1  | Abbot   |
| 2  | Doris   |
| 3  | Emerson |
| 4  | Green   |
| 5  | Jeames  |

Output:
| id | student |
|----|---------|
| 1  | Doris   |
| 2  | Abbot   |
| 3  | Green   |
| 4  | Emerson |
| 5  | Jeames  |

---

## 🔑 Key Insight
- Swap **odd ids with next even id**.
- Swap **even ids with previous odd id**.
- If the last id is odd and has no pair → keep it unchanged.
- Use `CASE WHEN` logic.

---

## ⚙️ Approach
1. Count total rows.
2. Use `CASE`:
   - If id is odd AND not last → `id + 1`
   - If id is even → `id - 1`
   - Else keep same id
3. Order by modified id.

---

## 🧩 Algorithm
1. Select from Seat table.
2. Use CASE conditions to compute new ordering id.
3. Order the result using swapped ids.

---

## ⏱️ Complexity
- **Time Complexity:** `O(n log n)` (due to sorting)
- **Space Complexity:** `O(1)`

---

