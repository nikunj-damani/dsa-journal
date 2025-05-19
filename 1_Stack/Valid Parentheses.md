---
created: 2025-05-19T15:38:00
parent: "[[DSA]]"
tags:
  - "#dsa/company/google"
  - "#dsa/difficulty/easy"
  - "#dsa/stack"
related:
---
## **LeetCode Link:** [#20](https://neetcode.io/problems/validate-parentheses/) 

## **Description**

You are given a string `s` consisting of the following characters: `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`.

The input string `s` is valid if and only if:

1. Every open bracket is closed by the same type of close bracket.
2. Open brackets are closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

Return `true` if `s` is a valid string, and `false` otherwise.

**Example 1:**

```java
Input: s = "[]"

Output: true
```


**Example 2:**

```java
Input: s = "([{}])"

Output: true
```


**Example 3:**

```java
Input: s = "[(])"

Output: false
```


Explanation: The brackets are not closed in the correct order.

**Constraints:**

- `1 <= s.length <= 1000`

## **Solution**

```python
class Solution:
	def isValid(self, s: str) -> bool:
		closeToOpen = {'}' : '{', ')' : '(', ']' : '['}
		stack = []
		
		for bracket in s:
			if stack and bracket in closeToOpen:
				if stack.pop() != closeToOpen[bracket]:
				return False
			else:
				stack.append(bracket)
		
		return True if not stack else False
```

### **Complexity:**

- **⚡ Time:** O(n)  
*Single pass through String*  

- **💾 Space:** O(n)  
*A stack to store open brackets*
