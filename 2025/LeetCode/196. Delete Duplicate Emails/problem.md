# 196. Delete Duplicate Emails

## Difficulty
Easy

## Topic
SQL, Delete, Group By

---

## Problem Statement

Write a SQL query to delete all duplicate email entries in a table named `Person`, keeping only the record with the smallest `id`.

Table: Person

| Column Name | Type |
|-------------|------|
| id          | int  |
| email       | varchar |

- `id` is the primary key.
- Each row contains an email address.
- Duplicate emails may exist.

The goal is to remove duplicate rows while retaining only the row with the minimum `id` for each email.

---

## Examples

### Example

Input:

Person table:

| id | email   |
|----|---------|
| 1  | a@b.com |
| 2  | c@d.com |
| 3  | a@b.com |

Output:

| id | email   |
|----|---------|
| 1  | a@b.com |
| 2  | c@d.com |

Explanation:
Row with `id = 3` is deleted because it has a duplicate email.

---

## Key Insight

- Duplicate emails share the same `email` value.
- We must keep the row with the smallest `id`.
- Any row with a larger `id` but same email should be deleted.
- Self-join is an efficient way to compare rows inside the same table.

---

## Approach (Self Join Delete)

1. Join the table with itself using email equality.
2. Compare ids of both rows.
3. Delete the row whose id is greater.

This ensures that only the smallest id remains for each email group.

---

## Algorithm

1. Use `DELETE` with alias.
2. Join `Person p1` with `Person p2`.
3. Match rows where `p1.email = p2.email`.
4. Delete rows where `p1.id > p2.id`.

---

## Complexity

Time Complexity: O(n²) in worst-case self comparison  
Space Complexity: O(1)

