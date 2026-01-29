# Students and Examinations

## Difficulty
Easy

## Topic
SQL, JOIN, Aggregation

## Problem Statement
You are given three tables: `Students`, `Subjects`, and `Examinations`.

Table: `Students`

| Column Name  | Type    |
|-------------|---------|
| student_id  | int     |
| student_name| varchar |

`student_id` is the primary key for this table.

---

Table: `Subjects`

| Column Name  | Type    |
|-------------|---------|
| subject_name| varchar |

`subject_name` is the primary key for this table.

---

Table: `Examinations`

| Column Name  | Type    |
|-------------|---------|
| student_id  | int     |
| subject_name| varchar |

This table may contain duplicate rows.

---

Write a SQL query to find the number of times each student attended each subject.

Return the result table ordered by `student_id` and `subject_name`.

---

## Examples

### Example 1

**Input:**

Students table:

| student_id | student_name |
|------------|--------------|
| 1          | Alice        |
| 2          | Bob          |
| 13         | John         |
| 6          | Alex         |

Subjects table:

| subject_name |
|--------------|
| Math         |
| Physics      |
| Programming  |

Examinations table:

| student_id | subject_name |
|------------|--------------|
| 1          | Math         |
| 1          | Physics      |
| 1          | Programming  |
| 2          | Programming  |
| 1          | Physics      |
| 1          | Math         |
| 13         | Math         |
| 13         | Programming  |
| 13         | Physics      |
| 2          | Math         |
| 1          | Math         |

**Output:**

| student_id | student_name | subject_name | attended_exams |
|------------|--------------|--------------|----------------|
| 1          | Alice        | Math         | 3              |
| 1          | Alice        | Physics      | 2              |
| 1          | Alice        | Programming  | 1              |
| 2          | Bob          | Math         | 1              |
| 2          | Bob          | Physics      | 0              |
| 2          | Bob          | Programming  | 1              |
| 6          | Alex         | Math         | 0              |
| 6          | Alex         | Physics      | 0              |
| 6          | Alex         | Programming  | 0              |
| 13         | John         | Math         | 1              |
| 13         | John         | Physics      | 1              |
| 13         | John         | Programming  | 1              |

---

## Key Insight
All student–subject combinations must be considered, even when a student has not attended a subject.

---

## Approach
1. Generate all possible combinations of students and subjects.
2. Attach examination records if they exist.
3. Count only the matching exam records.
4. Preserve combinations with zero attendance.
5. Sort the result as required.

---

## Algorithm
1. Perform a Cartesian product between students and subjects.
2. Join examination records based on student and subject.
3. Aggregate attendance counts.
4. Order the final result.

---

## Complexity
- **Time Complexity:** O(S × U)
- **Space Complexity:** O(1)

---

## Handwritten Notes
![notes](notes.jpg)

