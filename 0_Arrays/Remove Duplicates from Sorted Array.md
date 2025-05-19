# **Leetcode Link:** [#26](https://leetcode.com/problems/remove-duplicates-from-sorted-array/) | **Pattern:** Two Pointers

## Description

You are given an integer array `nums` sorted in **non-decreasing order**. Your task is to remove **duplicates** from `nums` **in-place** so that each element appears only once.

After removing the duplicates, return the number of unique elements, denoted as `k`, such that the **first `k` elements** of `nums` contain the unique elements.

Note:

- The order of the unique elements should remain the same as in the original array.
- It is not necessary to consider elements beyond the first `k` positions of the array.
- To be accepted, the first `k` elements of `nums` must contain all the unique elements.

Return `k` as the final result.

**Example 1:**

```java
Input: nums = [1,1,2,3,4]

Output: [1,2,3,4]
```

Explanation: You should return `k = 4` as we have four unique elements.

**Example 2:**

```java
Input: nums = [2,10,10,30,30,30]

Output: [2,10,30]
```

Explanation: You should return `k = 3` as we have three unique elements.

**Constraints:**

- `1 <= nums.length <= 30,000`
- `-100 <= nums[i] <= 100`
- `nums` is sorted in **non-decreasing** order.

## **Solution**
```python
class Solution:
    def removeDuplicates(self, nums: list[int]) -> int:
        l = 1
        for r in range(1, len(nums)):
            if nums[r] != nums[r - 1]:
                nums[l] = nums[r]
                l += 1
        return l
```

### **Complexity:**
- **⚡ Time:** O(n)  
*Single pass through array*  

- **💾 Space:** O(1)  
*Removed from same array no extra array*