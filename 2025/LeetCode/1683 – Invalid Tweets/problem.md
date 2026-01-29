# LeetCode 1683 – Invalid Tweets

**Difficulty:** Easy  
**Topic:** SQL, String Functions  

---

## Problem Statement
Table: `Tweets`

| Column Name | Type    |
|------------|---------|
| tweet_id   | int     |
| content    | varchar |

`tweet_id` is the primary key for this table.  
Each row contains a tweet.

Write an SQL query to **find the IDs of the invalid tweets**.  
A tweet is considered **invalid** if the **number of characters in `content` is strictly greater than 15**.

Return the result table in **any order**.

---

## Example

### Input
**Tweets table:**

| tweet_id | content                          |
|---------:|----------------------------------|
| 1        | Let us Code                      |
| 2        | More than fifteen chars are here |

### Output
| tweet_id |
|---------:|
| 2        |

---

## Approach
- Use a string length function to calculate the number of characters in `content`
- Filter tweets where the length is **greater than 15**
- Select only the `tweet_id`

---

## SQL Functions Used
- `LENGTH()` or `CHAR_LENGTH()` (depending on SQL dialect)

---

## Complexity
- **Time Complexity:** `O(n)`
- **Space Complexity:** `O(1)`

---

## Code
See `solution.sql`

---

## Handwritten Notes
![Notes](notes.jpg)

