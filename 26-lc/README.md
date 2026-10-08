# Remove Duplicates from Sorted Array

**LeetCode Problem:** [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

## Problem

Given an integer array `nums` sorted in **non-decreasing order**, remove the duplicates **in-place** such that each unique element appears only once.

Return the number of unique elements `k`.

The first `k` elements of `nums` should contain the unique elements in their original order.

### Example

```text
Input:
nums = [1,1,2]

Output:
2

Modified nums:
[1,2,_]
```

Another example:

```text
Input:
nums = [0,0,1,1,1,2,2,3,3,4]

Output:
5

Modified nums:
[0,1,2,3,4,_,_,_,_,_]
```

## Approach

This solution uses the **Two Pointer** technique.

We use two variables:

* `i` → points to the position of the last unique element.
* `j` → scans through the array looking for the next unique element.

Because the array is already sorted, duplicates are always next to each other.

### How it works

1. Start `i` at `0`.
2. Start `j` at `1`.
3. Compare `nums[j]` with `nums[i]`.
4. If they are different:

   * Move `i` forward.
   * Copy `nums[j]` to `nums[i]`.
5. Continue until `j` reaches the end.
6. Return `i + 1` because `i` represents the index of the last unique element.

## Solution

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int i = 0;

        for (int j = i + 1; j < nums.size(); j++) {
            if (nums[j] != nums[i]) {
                i++;
                nums[i] = nums[j];
            }
        }

        return i + 1;
    }
};
```

## Example Walkthrough

For:

```text
nums = [1,1,2,2,3]
```

Initially:

```text
i = 0
j = 1

[1,1,2,2,3]
 ↑ ↑
 i j
```

`nums[j] == nums[i]`, so we skip the duplicate.

Next:

```text
i = 0
j = 2

[1,1,2,2,3]
 ↑   ↑
 i   j
```

`nums[j] != nums[i]`.

Move `i` forward and copy:

```text
i = 1

nums[i] = nums[j]
```

Array becomes:

```text
[1,2,2,2,3]
```

Continue the same process.

Final result:

```text
[1,2,3,_,_]
```

And:

```text
k = 3
```

So the first `3` elements contain the unique values.

## Complexity

### Time Complexity

```text
O(n)
```

The array is traversed only once.

### Space Complexity

```text
O(1)
```

No additional array or data structure is used. The modification is done **in-place**.

## Key Concept

The main idea is:

> **Use one pointer to track the position of unique elements and another pointer to scan the array.**

This works efficiently because the input array is already sorted.
