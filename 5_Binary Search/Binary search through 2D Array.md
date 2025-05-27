## **LeetCode Link:** [#74](https://leetcode.com/problems/search-a-2d-matrix/) 

## **Description**

You are given an `m x n` 2-D integer array `matrix` and an integer `target`.

- Each row in `matrix` is sorted in _non-decreasing_ order.
- The first integer of every row is greater than the last integer of the previous row.

Return `true` if `target` exists within `matrix` or `false` otherwise.

Can you write a solution that runs in `O(log(m * n))` time?

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/7ca61f56-00d4-4fa0-26cf-56809028ac00/public)

```java
Input: matrix = [[1,2,4,8],[10,11,12,13],[14,20,30,40]], target = 10

Output: true
```

**Example 2:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/f25f2085-ce04-4447-9cee-f0a66c32a300/public)

```java
Input: matrix = [[1,2,4,8],[10,11,12,13],[14,20,30,40]], target = 15

Output: false
```

**Constraints:**

- `m == matrix.length`
- `n == matrix[i].length`
- `1 <= m, n <= 100`
- `-10000 <= matrix[i][j], target <= 10000`

## **Solution**
```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:

        top, bottom = 0, len(matrix) - 1

        while top <= bottom:
            mid = (top + bottom) // 2

            if target > matrix[mid][-1]:
                top = mid + 1
            elif target < matrix[mid][0]:
                bottom = mid - 1
            else:
                return (
                    self.binarySearch(0, len(matrix[mid]) - 1, matrix[mid], target)
                    != -1
                )

        return False

    def binarySearch(self, l: int, r: int, nums: List[int], target) -> int:
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
- **⚡ Time:** O(log m + log n)  
*Dividing columns log m and dividing rows log n*  

- **💾 Space:** O(1)  
*No extra variables used to store*
