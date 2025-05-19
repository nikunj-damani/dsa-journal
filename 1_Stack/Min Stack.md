
## **LeetCode Link:** [#155](https://leetcode.com/problems/min-stack/)

## **Description**
Design a stack class that supports the `push`, `pop`, `top`, and `getMin` operations.

- `MinStack()` initializes the stack object.
- `void push(int val)` pushes the element `val` onto the stack.
- `void pop()` removes the element on the top of the stack.
- `int top()` gets the top element of the stack.
- `int getMin()` retrieves the minimum element in the stack.

Each function should run in O(1)O(1) time.

**Example 1:**

```java
Input: ["MinStack", "push", 1, "push", 2, "push", 0, "getMin", "pop", "top", "getMin"]

Output: [null,null,null,null,0,null,2,1]

Explanation:
MinStack minStack = new MinStack();
minStack.push(1);
minStack.push(2);
minStack.push(0);
minStack.getMin(); // return 0
minStack.pop();
minStack.top();    // return 2
minStack.getMin(); // return 1
```

**Constraints:**

- `-2^31 <= val <= 2^31 - 1`.
- `pop`, `top` and `getMin` will always be called on **non-empty** stacks.

## **Solution**
```python
class MinStack:
    def __init__(self):
        self.stack = []
        self.minStack = []

    def push(self, val: int) -> None:
        self.stack.append(val)
        
        if not self.minStack or self.minStack[-1] > val:
			self.minStack.append(val)
		else:
			self.minStack.append(self.minStack[-1])
			
    def pop(self) -> None:
        self.stack.pop()
        self.minStack.pop()

    def top(self) -> int:
        return self.stack[-1]

    def getMin(self) -> int:
        return self.minStack[-1]
```


### **Explanation**:

- `stack`: Stores all pushed values.
    
- `minStack`: Keeps track of the **minimum** element at every level.
    
    - On `push`: add the **min(val, current_min)**.
        
    - On `pop`: remove from both stacks.
        
- Always have the current **minimum at the top of `minStack`**.

### **Complexity:**
- **⚡ Time:** O(1)  
*Each operation takes constant time*  

- **💾 Space:** O(n)  
*Used two stacks which can be max size of n*
