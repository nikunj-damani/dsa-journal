## **NeetCode Link:** (https://neetcode.io/problems/mergeSort)

## **Description**

_**Merge Sort**_ is a divide-and-conquer algorithm for sorting an array or list of elements. It works by recursively dividing the unsorted list into `n` sub-lists, each containing one element. Then, it repeatedly merges sub-lists to produce new sorted sub-lists until there is only one sub-list remaining.

**Objective:**

Given a list of key-value pairs, sort the list by `key` using _**Merge Sort**_. If two key-value pairs have the same `key`, maintain their relative order in the sorted list.

**Input:**

- `pairs` - a list of key-value pairs, where each key-value has an integer `key` and a string `value`. `(0 <= pairs.length <= 100)`.

**Example 1:**

```java
Input:
pairs = [(5, "apple"), (2, "banana"), (9, "cherry"), (1, "date"), (9, "elderberry")]

Output:
[(1, "date"), (2, "banana"), (5, "apple"), (9, "cherry"), (9, "elderberry")]
```

Note: As you can see, the solution is _always_ stable. The two pairs with the key 9 maintained their relative positions.

## **Solution - 1 (Extra Space)**

```python
# Definition for a pair.
# class Pair:
#     def __init__(self, key: int, value: str):
#         self.key = key
#         self.value = value
class Solution:
    def mergeSort(self, pairs: List[Pair]) -> List[Pair]:
        return self.mergeSortHelper(pairs)

    def mergeSortHelper(self, pairs: List[Pair]) -> List[Pair]:
        if len(pairs) <= 1:
            return pairs

        m = len(pairs) // 2

        left = self.mergeSortHelper(pairs[:m])
        right = self.mergeSortHelper(pairs[m:])

        return self.merge(left, right)

    def merge(self, left: List[Pair], right: List[Pair]) -> List[Pair]:
        result = []

        i = j = 0

        while i < len(left) and j < len(right):
            if left[i].key <= right[j].key:
                result.append(left[i])
                i += 1
            else:
                result.append(right[j])
                j += 1

        result.extend(left[i:])
        result.extend(right[j:])

        return result
```

### **Complexity:**
- **⚡ Time:** O(n log n)  
*n comparison operations are performed at each level and log n  steps to splitting*

- **💾 Space:** O(n)  
*Result array to store sorting*


## **Solution - 2 (No Extra Space)**

```python
# Definition for a pair.
# class Pair:
#     def __init__(self, key: int, value: str):
#         self.key = key
#         self.value = value
class Solution:
    def mergeSort(self, pairs: List[Pair]) -> List[Pair]:
        return self.mergeSortHelper(pairs, 0, len(pairs) - 1)

    def mergeSortHelper(self, pairs: List[Pair], s: int, e: int) -> List[Pair]:
        if e - s + 1 <= 1:
            return pairs

        m = (s + e) // 2

        self.mergeSortHelper(pairs, s, m)
        self.mergeSortHelper(pairs, m + 1, e)

        return self.merge(pairs, s, m, e)

    def merge(self, arr: List[Pair], s: int, m: int, e: int) -> List[Pair]:
        i = j = 0
        k = s

        left = arr[s : m + 1]
        right = arr[m + 1 : e + 1]

        while i < len(left) and j < len(right):
            if left[i].key <= right[j].key:
                arr[k] = left[i]
                i += 1
            else:
                arr[k] = right[j]
                j += 1
            k += 1

        while i < len(left):
            arr[k] = left[i]
            i += 1
            k += 1

        while j < len(right):
            arr[k] = right[j]
            j += 1
            k += 1

        return arr
```


### **Complexity:**
- **⚡ Time:** O(n log n)  
*n comparison operations are performed at each level and log n  steps to splitting*

- **💾 Space:** O(1)  
*Used only temp variables for left and right, no extra space*

