# 1527. Patients With a Condition

**Difficulty:** Easy  
**Topics:** SQL, String Matching  

---

## 🧾 Problem Statement
Table: `Patients`

| Column Name | Type    |
|-------------|---------|
| patient_id  | int     |
| patient_name| varchar |
| conditions  | varchar |

- `patient_id` is the primary key.
- `conditions` contains 0 or more medical conditions separated by spaces.

Write an SQL query to report the `patient_id`, `patient_name`, and `conditions` of the patients who have **Type I Diabetes**, whose condition code always starts with:


DIAB1

Return the result table in **any order**.

---

## 📥 Example

**Input**
```

Patients table:

+------------+--------------+--------------+
| patient_id | patient_name | conditions   |
+------------+--------------+--------------+
| 1          | Daniel       | YFEV COUGH   |
| 2          | Alice        | DIAB100 MYOP |
| 3          | Bob          | ACNE DIAB100 |
| 4          | George       | DIAB201      |
+------------+--------------+--------------+

```

**Output**
```

+------------+--------------+--------------+
| patient_id | patient_name | conditions   |
+------------+--------------+--------------+
| 2          | Alice        | DIAB100 MYOP |
| 3          | Bob          | ACNE DIAB100 |
+------------+--------------+--------------+

```

---

## 🔑 Key Insight
- We need rows where a condition **starts with `DIAB1`**.
- The code may appear:
  - At the beginning of the string
  - After a space inside the string

So we check:

conditions LIKE 'DIAB1%'
OR conditions LIKE '% DIAB1%'

---

## 🚀 Approach
1. Use SQL `LIKE` pattern matching.
2. Match:
   - Beginning of string → `'DIAB1%'`
   - After space → `'% DIAB1%'`

---

## 🧩 Algorithm

SELECT required columns
FROM Patients
WHERE conditions starts with DIAB1
OR conditions contains " DIAB1"

---

## ⏱ Complexity Analysis

Time Complexity: O(N)
Space Complexity: O(1)

---

