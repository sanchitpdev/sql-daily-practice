# 1341. Movie Rating

**Difficulty:** Medium  
**Topic:** SQL, JOIN, GROUP BY, Aggregation, Subquery

---

## 🧾 Problem Statement

You are given three tables:

### **Movies**
| Column Name | Type |
|---|---|
| movie_id | int |
| title | varchar |

### **Users**
| Column Name | Type |
|---|---|
| user_id | int |
| name | varchar |

### **MovieRating**
| Column Name | Type |
|---|---|
| movie_id | int |
| user_id | int |
| rating | int |
| created_at | date |

---

Write an SQL query to:

1. Find the **name of the user** who has rated the **greatest number of movies**.  
   - If there is a tie, return the **lexicographically smaller name**.

2. Find the **movie title** with the **highest average rating** in **February 2020**.  
   - If there is a tie, return the **lexicographically smaller title**.

Return the result as:

| results |
|---|
| user_name |
| movie_title |

---

## 🧪 Examples

### Input
Movies
```
+----------+-------------+
| movie_id | title       |
+----------+-------------+
| 1        | Avengers    |
| 2        | Frozen 2    |
| 3        | Joker       |
+----------+-------------+
```

Users
```
+---------+--------+
| user_id | name   |
+---------+--------+
| 1       | Daniel |
| 2       | Monica |
| 3       | Maria  |
+---------+--------+
```

MovieRating
```
+----------+---------+--------+------------+
| movie_id | user_id | rating | created_at |
+----------+---------+--------+------------+
| 1        | 1       | 3      | 2020-01-12 |
| 1        | 2       | 4      | 2020-02-11 |
| 1        | 3       | 2      | 2020-02-12 |
| 2        | 1       | 5      | 2020-02-17 |
| 2        | 2       | 2      | 2020-02-01 |
| 3        | 1       | 3      | 2020-02-22 |
| 3        | 3       | 4      | 2020-02-25 |
+----------+---------+--------+------------+
```

### Output
```
+---------+
| results |
+---------+
| Daniel  |
| Frozen 2|
+---------+
```

---

## 💡 Key Insight

This problem is basically **two independent queries combined with UNION ALL**:

- Part 1 → Count ratings per user → pick max count.
- Part 2 → Average rating per movie (only Feb 2020) → pick max avg.

Tie-breaking is handled using:

```
ORDER BY value DESC, name ASC
```

---

## ⚙️ Approach

### ✅ Step 1 — Most Active User
- Join `Users` with `MovieRating`.
- Count ratings per user.
- Sort by:
  - count DESC
  - name ASC
- Take top 1.

### ✅ Step 2 — Best Movie in Feb 2020
- Filter `created_at` between `2020-02-01` and `2020-02-29`.
- Join `Movies` with `MovieRating`.
- Calculate `AVG(rating)`.
- Sort by:
  - avg DESC
  - title ASC
- Take top 1.

### ✅ Step 3 — Combine Results
Use `UNION ALL` to stack both results vertically.

---

## 🧩 Algorithm

1. Aggregate rating count grouped by `user_id`.
2. Order and limit to get top user.
3. Filter February ratings.
4. Compute average grouped by `movie_id`.
5. Order and limit to get top movie.
6. Merge outputs.

---

## ⏱️ Complexity

- Aggregation on ratings table: **O(N)**
- Sorting groups: **O(U log U + M log M)**

Where:
- `N` = ratings count
- `U` = users
- `M` = movies

---
