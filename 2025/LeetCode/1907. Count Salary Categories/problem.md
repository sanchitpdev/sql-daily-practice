# 1907. Count Salary Categories

**Difficulty:** Easy  
**Topic:** SQL, Aggregation, Conditional Counting  

---

## Problem Statement

Table: `Accounts`

| Column Name | Type |
|------------|------|
| account_id | int |
| income | int |

Write an SQL query to report the number of accounts in the following salary categories:

- **Low Salary**: income < 20000  
- **Average Salary**: 20000 ≤ income ≤ 50000  
- **High Salary**: income > 50000  

The result table must contain all three categories **in the following order**:
1. Low Salary  
2. Average Salary  
3. High Salary  

If there are no accounts in a category, return `0` for that category.

---

## Example

### Input
`Accounts` table:

| account_id | income |
|------------|--------|
| 3 | 108939 |
| 2 | 12747 |
| 8 | 87709 |
| 6 | 91796 |

### Output

| category | accounts_count |
|--------|----------------|
| Low Salary | 1 |
| Average Salary | 0 |
| High Salary | 3 |

---

## Key Insight

- Salary categories are **fixed**, not dynamic.
- Using `GROUP BY` may skip categories with zero count.
- `UNION ALL` ensures **all categories appear** in the output.
- Order matters → query must explicitly control output order.

---

## Approach

- Count accounts separately for each salary range.
- Assign category names manually.
- Combine results using `UNION ALL`.

---

## Algorithm

1. Select count of accounts where `income < 20000` and label as **Low Salary**
2. Select count of accounts where `income BETWEEN 20000 AND 50000` and label as **Average Salary**
3. Select count of accounts where `income > 50000` and label as **High Salary**
4. Combine all three results using `UNION ALL`

---

