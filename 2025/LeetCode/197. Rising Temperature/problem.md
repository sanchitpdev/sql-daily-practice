# LeetCode 197 – Rising Temperature

**Difficulty:** Easy  
**Topic:** SQL, Self Join  

---

## Problem Statement
You are given a table `Weather` that stores daily temperature records.

Each row contains:
- `id` – unique identifier
- `recordDate` – the date of the record
- `temperature` – temperature on that day

The task is to find the `id` of days where the temperature was **higher than the previous day**.

The result can be returned in **any order**.

---

## Key Insight
To check whether the temperature increased, each day must be **compared with its previous day**.  
Since both records belong to the **same table**, the comparison is done logically using a **self join concept**.

---

## Approach
- Consider the table as two logical views:
  - one representing the **current day**
  - one representing the **previous day**
- Match rows where the current day is exactly **one day after** the previous day
- From these matched pairs, keep only those where:
  - the current day’s temperature is higher
- Return the `id` of the current day

---

## Algorithm
1. Compare each day with the previous day
2. Ensure the dates are consecutive
3. Check if the temperature increased
4. Collect the ids of such days

---

## Complexity
- **Time Complexity:** O(n²)
- **Space Complexity:** O(1)

---

## Handwritten Notes
![Notes](notes.jpg)

