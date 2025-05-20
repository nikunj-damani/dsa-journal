## **LeetCode Link:** [#21](https://neetcode.io/problems/merge-two-sorted-linked-lists/) 

## **Solution**
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def mergeTwoLists(self, list1: ListNode, list2: ListNode) -> ListNode:
        dummy = node = ListNode()

        while list1 and list2:
            if list1.val < list2.val:
                node.next = list1
                list1 = list1.next
            else:
                node.next = list2
                list2 = list2.next
            node = node.next

        if l1:
			tail.next = l1
		if l2:
		tail.next = l2

        return dummy.next
```

### **Complexity:**
- **⚡ Time:** O(n)  
*Iterating through smaller linked list*  

- **💾 Space:** O(1)  
*Only 2 variables used*
