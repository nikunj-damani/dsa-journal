## **LeetCode Link:** [#206](https://leetcode.com/problems/reverse-linked-list/)

## **Description**

Given the beginning of a singly linked list `head`, reverse the list, and return the new beginning of the list.

**Example 1:**

```java
Input: head = [0,1,2,3]

Output: [3,2,1,0]
```

**Example 2:**

```java
Input: head = []

Output: []
```

**Constraints:**

- `0 <= The length of the list <= 1000`.
- `-1000 <= Node.val <= 1000`

## **Solution**
```python
class Solution:
	def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
		prev, curr = None, head

		while curr:		
			temp = curr.next
			curr.next = prev			
			prev = curr
			curr = temp
  
		return prev
```

### **Complexity:**
- **⚡ Time:** O(n)  
*Single pass through linked list*  

- **💾 Space:** O(1)  
*Only 2 variables used*
