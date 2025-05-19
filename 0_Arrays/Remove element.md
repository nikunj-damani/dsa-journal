## **Leetcode Link:** [#27](https://neetcode.io/problems/remove-element/) | **Pattern:** Two Pointers  

## **Description**

You are given an integer array `nums` and an integer `val`. Your task is to remove **all occurrences** of `val` from `nums` **in-place**.

After removing all occurrences of `val`, return the number of remaining elements, say `k`, such that the **first `k` elements** of `nums` do **not contain `val`**.

Note:

- The order of the elements which are not equal to `val` **does not matter**.
- It is not necessary to consider elements beyond the first `k` positions of the array.
- To be accepted, the first `k` elements of `nums` must contain only elements **not equal** to `val`.

Return `k` as the final result.

**Example 1:**

```java
Input: nums = [1,1,2,3,4], val = 1

Output: [2,3,4]
```

Copy

Explanation: You should return `k = 3` as we have `3` elements which are not equal to `val = 1`.

**Example 2:**

```java
Input: nums = [0,1,2,2,3,0,4,2], val = 2

Output: [0,1,3,0,4]
```

Copy

Explanation: You should return `k = 5` as we have `5` elements which are not equal to `val = 2`.

**Constraints:**

- `0 <= nums.length <= 100`
- `0 <= nums[i] <= 50`
- `0 <= val <= 100`
## **Solution**
```python
class Solution:
    def removeElement(self, nums: list[int], val: int) -> int:
        k = 0
        for i in range(len(nums)):
            if nums[i] != val:
                nums[k] = nums[i]
                k += 1
        return k
```

### **Complexity:**
- **⚡ Time:** O(n)  
*Single pass through array*  

- **💾 Space:** O(1)  
*Removed from same array no extra array*
