# Not Boring Movies

## Difficulty
Easy

## Topic
SQL, WHERE, ORDER BY

## Problem Statement
Table: `Cinema`

| Column Name | Type    |
|------------|---------|
| id         | int     |
| movie      | varchar |
| description| varchar |
| rating     | float   |

`id` is the primary key for this table.

Write a SQL query to report the movies with **odd-numbered IDs** and a **description that is not 'boring'**.

Return the result table ordered by `rating` in **descending order**.

---

## Examples

### Example 1
**Input**

Cinema
+----+------------+-------------+--------+
| id | movie      | description | rating |
+----+------------+-------------+--------+
| 1  | War        | great 3D    | 8.9    |
| 2  | Science    | fiction     | 8.5    |
| 3  | irish      | boring      | 6.2    |
| 4  | Ice song   | Fantacy     | 8.6    |
| 5  | House card | Interesting | 9.1    |
+----+------------+-------------+--------+

**Output**
+----+------------+-------------+--------+
| id | movie      | description | rating |
+----+------------+-------------+--------+
| 5  | House card | Interesting | 9.1    |
| 1  | War        | great 3D    | 8.9    |
+----+------------+-------------+--------+
---

## Key Insight
- Use modulo operation to filter **odd IDs**
- Exclude rows where `description = 'boring'`
- Sort results using `ORDER BY rating DESC`

---

## Approach
Filter the rows using `WHERE` conditions and then sort the result set.

---

## Algorithm
1. Select records from the `Cinema` table
2. Filter rows where `id` is odd
3. Exclude movies with description `'boring'`
4. Sort the remaining rows by `rating` in descending order

---

## Complexity
Time: O(n)  
Space: O(1)

---

## Code Reference
solution.sql

---

## Handwritten Notes
notes.jpg
