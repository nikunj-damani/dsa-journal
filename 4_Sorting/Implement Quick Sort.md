## **NeetCode Link:** (https://neetcode.io/problems/quickSort)

## **Description**
Quick Sort is a divide-and-conquer sorting algorithm that works by partitioning an array into two smaller sub-arrays based on a pivot element. The elements less than the pivot go to the left sub-array and those greater go to the right sub-array. The algorithm then recursively sorts the sub-arrays.

Objective:

Given a list of key-value pairs, sort the list by key using Quick Sort. For each partitioning step:

Use the right-most element as the pivot.
Elements less than the pivot should be placed to the left of the pivot, and elements greater than or equal to the pivot should be placed to the right of the pivot.
The correctness of your solution will be determined based on these requirements.

Input:

pairs - a list of key-value pairs, where each key-value has an integer key and a string value. (0 <= pairs.length <= 100).
Example 1:

Input:
pairs = [(3, "cat"), (2, "dog"), (3, "bird")]

Output:
[(2, "dog"), (3, "bird"), (3, "cat")]

## **Solution**
```python
# Definition for a pair.
# class Pair:
#     def __init__(self, key: int, value: str):
#         self.key = key
#         self.value = value
class Solution:
    def quickSort(self, pairs: List[Pair]) -> List[Pair]:
        self.quickSortHelper(pairs, 0, len(pairs) - 1)
        return pairs

    def quickSortHelper(self, pairs, s: int, e: int) -> None:

        if e - s + 1 <= 1:
            return pairs

        left = s
        pivot = pairs[e]

        for i in range(s, e):
            if pairs[i].key < pivot.key:
                temp = pairs[i]
                pairs[i] = pairs[left]
                pairs[left] = temp
                left += 1

        pairs[e], pairs[left] = pairs[left], pivot

        self.quickSortHelper(pairs, s, left - 1)
        self.quickSortHelper(pairs, left + 1, e)

```


### **Complexity:**
- **⚡ Time:** Worst: O(n^2) Average: O(nlogn)  
*depends on the input array and pivot value*  

- **💾 Space:** O(1)  
*sorted in same array*
