# LeetCode 2356 – Number of Unique Subjects Taught by Each Teacher

**Difficulty:** Easy  
**Topic:** SQL, Aggregation  

---

## Problem Statement

You are given a table **Teacher** with the following columns:

- `teacher_id` – ID of the teacher  
- `subject_id` – ID of the subject  
- `dept_id` – ID of the department  

Each row indicates that a teacher teaches a subject in a department.

Write an SQL query to report the number of **unique subjects** each teacher teaches.

Return the result table in **any order**.

---

## Table Schema

Teacher(
  teacher_id INT,
  subject_id INT,
  dept_id INT
)
---

## Example

### Input
```
| teacher_id | subject_id | dept_id |
| ---------- | ---------- | ------- |
| 1          | 2          | 3       |
| 1          | 2          | 4       |
| 1          | 3          | 3       |
| 2          | 1          | 1       |
| 2          | 2          | 1       |
| 2          | 3          | 1       |
| 2          | 4          | 1       |
```
### Output
```
| teacher_id | cnt |
| ---------- | --- |
| 1          | 2   |
| 2          | 4   |
```
---

## Key Insight

* A teacher may teach the **same subject in multiple departments**.
* We must count **distinct `subject_id` per `teacher_id`**, not total rows.
* This is a classic use case of `COUNT(DISTINCT ...)` with `GROUP BY`.

---

## Approach

1. Group records by `teacher_id`.
2. Count distinct `subject_id` for each teacher.
3. Alias the count as `cnt`.

---

## Algorithm

1. Select `teacher_id`.
2. Use `COUNT(DISTINCT subject_id)` to count unique subjects.
3. Group the result by `teacher_id`.

---

## Complexity Analysis

* **Time Complexity:** O(n), where `n` is the number of rows in the table
* **Space Complexity:** O(1), excluding output table

---

