# 602. Friend Requests II: Who Has the Most Friends

**Difficulty:** Medium  
**Topic:** SQL, Aggregation, UNION ALL, GROUP BY

---

## 🧾 Problem Statement
Table: `RequestAccepted`

| Column Name   | Type |
|---|---|
| requester_id | int |
| accepter_id  | int |
| accept_date  | date |

This table records the friend requests that have been accepted.

Write an SQL query to find the person who has the **most friends** and the number of friends they have.

Friendship is **bidirectional**, meaning if A is a friend of B, then B is also a friend of A.

Return the result table in the format:

| id | num |

Where:
- `id` = person with the most friends  
- `num` = total number of friends

If multiple people have the same maximum number, return any one of them.

---

## 📌 Example

**Input:**

RequestAccepted

| requester_id | accepter_id | accept_date |
|---|---|---|
| 1 | 2 | 2016/06/03 |
| 1 | 3 | 2016/06/08 |
| 2 | 3 | 2016/06/08 |

**Output:**

| id | num |
|---|---|
| 3 | 2 |

---

## 🔑 Key Insight
- Friendship is **two-way**.
- Each accepted request creates **two relationships**:
  - requester → accepter
  - accepter → requester
- We must count total appearances of each user in both roles.

---

## 🧠 Approach
1. Convert friendships into a single column (`id`) using `UNION ALL`.
2. Include:
   - requester_id as id
   - accepter_id as id
3. Group by `id`.
4. Count total friends.
5. Sort by count in descending order.
6. Return the top result.

---

## ⚙️ Algorithm
1. Select requester_id as id.
2. UNION ALL with accepter_id as id.
3. GROUP BY id.
4. COUNT total rows per id.
5. ORDER BY count DESC.
6. LIMIT 1.

---

## ⏱ Complexity
- **Time Complexity:** O(n)  
- **Space Complexity:** O(n) (temporary union result)

---

