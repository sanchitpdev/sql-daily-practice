# 596. Classes More Than 5 Students

Difficulty: Easy  
Topic: SQL, Group By  

---

## Problem Statement

Table: `Courses`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| student     | varchar |
| class       | varchar |
+-------------+---------+
````

(student, class) is the primary key for this table.

Write a SQL query to find all classes that have **at least 5 students**.

Return the result table in any order.

---

## Examples

Example 1:

Input:

Courses table:

```
+---------+----------+
| student | class    |
+---------+----------+
| A       | Math     |
| B       | English  |
| C       | Math     |
| D       | Biology  |
| E       | Math     |
| F       | Computer |
| G       | Math     |
| H       | Math     |
| I       | Math     |
+---------+----------+
```

Output:

```
+---------+
| class   |
+---------+
| Math    |
+---------+
```

Explanation:

Math has 6 students, so it is included.

---

## Key Insight

To find classes with at least 5 students:

* Group rows by `class`
* Count the number of students in each class
* Filter groups using `HAVING`

---

## Approach

1. Group by `class`
2. Count students in each group
3. Use `HAVING COUNT(student) >= 5`

---

## Algorithm

1. Select `class`
2. Group by `class`
3. Keep only those groups where student count is 5 or more

---

## Complexity

Time Complexity:

O(n)

Space Complexity:

O(1)

---

