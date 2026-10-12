# 1. Two Sum

**LeetCode Problem:** [Two Sum](https://leetcode.com/problems/two-sum/)  
**Difficulty:** Easy  
**Topics:** Array, Brute Force

## Problem Description

Given an array of integers `nums` and an integer `target`, return the indices of the two numbers whose sum equals the target.

- Each input has exactly one solution.
- The same element cannot be used twice.
- The answer can be returned in any order.

## Approach: Brute Force

1. Use an outer loop to select the first element.
2. Use an inner loop starting at `i + 1` to select the second element.
3. Check whether `nums[i] + nums[j] == target`.
4. If the sum equals the target, return `{i, j}`.
5. If no pair is found, return an empty vector.

## Code (C++)

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        for (int i = 0; i < nums.size() - 1; i++) {
            for (int j = i + 1; j < nums.size(); j++) {
                if (nums[i] + nums[j] == target)
                    return {i, j};
            }
        }
        return {};
    }
};
```

## Examples

| Input | Output | Explanation |
|---|---|---|
| `nums = [2,7,11,15]`, `target = 9` | `[0,1]` | `2 + 7 = 9` |
| `nums = [3,2,4]`, `target = 6` | `[1,2]` | `2 + 4 = 6` |
| `nums = [3,3]`, `target = 6` | `[0,1]` | `3 + 3 = 6` |

## Complexity Analysis

- **Time Complexity:** `O(n²)` — Two nested loops compare pairs of elements.
- **Space Complexity:** `O(1)` auxiliary space — Only a constant number of extra variables are used, excluding the returned vector.

## Key Takeaway

The brute-force approach checks every possible pair until it finds the target sum. Starting the inner loop at `i + 1` prevents using the same element twice and avoids checking duplicate pairs.
