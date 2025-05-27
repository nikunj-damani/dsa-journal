## **NeetCode Link:** (https://neetcode.io/solutions/binary-search) 

## **Description**

You are given an array of **distinct** integers `nums`, sorted in ascending order, and an integer `target`.

Implement a function to search for `target` within `nums`. If it exists, then return its index, otherwise, return `-1`.

Your solution must run in O(logn) time.

**Example 1:**

```java
Input: nums = [-1,0,2,4,6,8], target = 4

Output: 3
```


**Example 2:**

```java
Input: nums = [-1,0,2,4,6,8], target = 3

Output: -1
```


**Constraints:**

- `1 <= nums.length <= 10000`.
- `-10000 < nums[i], target < 10000`

## **Solution - Iteration**
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:

        l, r = 0, len(nums) - 1

        while l <= r:
            m = (l + r) // 2

            if nums[m] < target:
                l = m + 1
            elif nums[m] > target:
                r = m - 1
            else:
                return m

        return -1
```

## **Solution - Recursion**
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        return self.binarySearch(0, len(nums) - 1, nums, target)

    def binarySearch(self, l: int, r: int, nums: [List], target) -> int:
        if l > r:
            return -1

        m = l + ((r - l) // 2)

        if target > nums[m]:
            return self.binarySearch(m + 1, r, nums, target)
        elif target < nums[m]:
            return self.binarySearch(l, m - 1, nums, target)
        else:
            return m
```


### **Complexity:**
- **⚡ Time:** O(logn)  
*Doing binary search by dividing array in halves*  

- **💾 Space:** O(1)  
*No extra variables used*
