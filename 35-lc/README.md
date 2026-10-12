# 35. Search Insert Position

**LeetCode Problem:** [Search Insert Position](https://leetcode.com/problems/search-insert-position/)  
**Difficulty:** Easy  
**Topic:** Array, Binary Search

## Problem Description

Given a sorted array of distinct integers and a target value, return the index if the target is found. Otherwise, return the index where the target should be inserted to maintain the sorted order.

The algorithm must run in **O(log n)** time complexity.

## Approach: Binary Search

1. Initialize `left = 0` and `right = nums.size() - 1`.
2. Calculate the middle index using `left + (right - left) / 2`.
3. If `nums[mid] == target`, return `mid`.
4. If `nums[mid] < target`, search the right half by updating `left = mid + 1`.
5. Otherwise, search the left half by updating `right = mid - 1`.
6. If the target is not found, return `left`, which represents the correct insertion position.

## Code (C++)

```cpp
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int left = 0, right = nums.size() - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] == target)
                return mid;
            else if (nums[mid] < target)
                left = mid + 1;
            else
                right = mid - 1;
        }

        return left;
    }
};
```

## Examples

| Input | Output | Explanation |
|---|---|---|
| `nums = [1,3,5,6]`, `target = 5` | `2` | Target exists at index 2. |
| `nums = [1,3,5,6]`, `target = 2` | `1` | Target should be inserted at index 1. |
| `nums = [1,3,5,6]`, `target = 7` | `4` | Target should be inserted at the end. |

## Complexity Analysis

- **Time Complexity:** `O(log n)` — Binary search eliminates half of the search space in each iteration.
- **Space Complexity:** `O(1)` — Only a constant number of extra variables are used.

## Key Takeaway

Binary search works efficiently on sorted arrays. When the target is not found, `left` points to the correct insertion index.
