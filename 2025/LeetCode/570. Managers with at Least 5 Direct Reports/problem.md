md
# Two Sum II - Input Array Is Sorted

## Difficulty
Medium

## Topic
Array, Two Pointers, Binary Search

## Problem Statement
Given a **1-indexed** array of integers `numbers` that is already sorted in **non-decreasing order**, find two numbers such that they add up to a specific `target` number.

Let these two numbers be `numbers[index1]` and `numbers[index2]` where:

- `1 <= index1 < index2 <= numbers.length`
- `numbers[index1] + numbers[index2] == target`

Return the indices of the two numbers **added by one** as an integer array `[index1, index2]` of length 2.

The problem guarantees that **exactly one solution exists**, and you may **not** use the same element twice.

---

## Examples

### Example 1

**Input:**

numbers = [2,7,11,15], target = 9

**Output:**

[1,2]

---

### Example 2

**Input:**

numbers = [2,3,4], target = 6


**Output:**

[1,3]

---

### Example 3

**Input:**

numbers = [-1,0], target = -1

**Output:**

[1,2]

---

## Key Insight
The array is sorted, which allows reducing the search space by adjusting indices instead of checking all pairs.

---

## Approach
1. Use the sorted nature of the array.
2. Maintain two indices at different positions.
3. Compare the sum with the target.
4. Adjust indices until the valid pair is found.

---

## Algorithm
1. Place one index at the start and one at the end.
2. Compute the sum of both values.
3. If the sum is smaller than the target, move the left index forward.
4. If the sum is larger than the target, move the right index backward.
5. Stop when the target sum is achieved.

---

## Complexity
- **Time Complexity:** O(n)
- **Space Complexity:** O(1)

---

## Handwritten Notes
![notes](notes.jpg)

