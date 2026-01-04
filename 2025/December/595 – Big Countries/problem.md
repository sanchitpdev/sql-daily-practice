# LeetCode 595 – Big Countries

**Difficulty:** Easy  
**Topic:** SQL, Filtering  

## Problem Statement
You are given a table `World`.

Write an SQL query to find the **name, population, and area** of countries that are considered **big**.

A country is considered big if:
- it has an area of at least **3,000,000** square kilometers, OR
- it has a population of at least **25,000,000**

## Approach
- Select the `name`, `population`, and `area` columns from the `World` table
- Filter records using the `WHERE` clause
- Use the `OR` condition to check:
  - `area >= 3000000`
  - OR `population >= 25000000`

## Complexity
- Time: O(n)
- Space: O(1)

## Code
See `solution.sql`

## Handwritten Notes
![Notes](notes.jpg)

