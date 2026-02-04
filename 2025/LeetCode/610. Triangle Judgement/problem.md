# LeetCode 610 — Triangle Judgement

## Problem
Given a table `Triangle` with columns `x`, `y`, `z`,  
check if these three sides can form a triangle.

A triangle is valid if:

- x + y > z  
- x + z > y  
- y + z > x  

Return "Yes" if valid, otherwise "No".

---

## Example

Input:
| x | y | z |
|---|---|---|
| 3 | 4 | 5 |

Output:
| triangle |
|----------|
| Yes      |

---

## Idea
Use `CASE` statement to test the triangle condition.

---

