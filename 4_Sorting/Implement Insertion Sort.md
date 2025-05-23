## **NeetCode Link:** (https://neetcode.io/problems/insertionSort) 

## **Description**

Implement Insertion Sort and return intermediate states.

_**Insertion Sort**_ is a simple sorting algorithm that builds the sorted list one element at a time, from left to right. It works by repeatedly taking an element from the unsorted portion and inserting it into its correct position in the sorted portion of the list.

**Objective:**

Given a list of key-value pairs, sort the list by `key` using _**Insertion Sort**_. Return a list of lists showing the state of the array after each insertion. If two key-value pairs have the same `key`, maintain their relative order in the sorted list.

**Input:**

- `pairs` - a list of key-value pairs, where each key-value has an integer `key` and a string `value`. `(0 <= pairs.length <= 100)`.

**Example 1:**

```java
Input:
pairs = [(5, "apple"), (2, "banana"), (9, "cherry")]

Output:
[[(5, "apple"), (2, "banana"), (9, "cherry")], 
 [(2, "banana"), (5, "apple"), (9, "cherry")], 
 [(2, "banana"), (5, "apple"), (9, "cherry")]]
```

Notice that the output shows the state of the array after each insertion. The last state is the final sorted array. There should be `pairs.length` states in total.

## **Solution**

```python
# Definition for a pair.
# class Pair:
#     def __init__(self, key: int, value: str):
#         self.key = key
#         self.value = value
class Solution:
    def insertionSort(self, pairs: List[Pair]) -> List[List[Pair]]:
        n = len(pairs)
        res = []
        
        for i in range(n):
            j = i - 1

            while j >= 0 and pairs[j].key > pairs[j + 1].key:
                pairs[j], pairs[j + 1] = pairs[j + 1], pairs[j]
                j -= 1
            
            res.append(pairs[:])

        return res
```

### **Complexity:**
- **⚡ Time:** O(n ^ 2)  
*Need to compare each element with other element to compare*  

- **💾 Space:** O(n)  
*Storing n pairs a variable*
