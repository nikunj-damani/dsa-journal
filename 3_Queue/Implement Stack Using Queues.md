## **LeetCode Link:** [#225](https://leetcode.com/problems/implement-stack-using-queues/)

## **Description**

Implement a **last-in-first-out (LACK)** stack using **only two queues**. The implemented stack should support standard operations:

- `push(x)` – Push element `x` onto the stack.
    
- `pop()` – Remove and return the top element.
    
- `top()` – Get the top element without removing it.
    
- `empty()` – Return whether the stack is empty.

## **Solution**
```python
class MyStack:

    def __init__(self):
        self.q1 = deque()
        self.q2 = deque()

    def push(self, x: int) -> None:
        self.q2.append(x)
        while self.q1:
            self.q2.append(self.q1.popleft())
        
        self.q1, self.q2 = self.q2, self.q1

    def pop(self) -> int:
        return self.q1.popleft()

    def top(self) -> int:
        return self.q1[0]

    def empty(self) -> bool:
        return len(self.q1) == 0
```

### **Complexity:**
- **⚡ Time:** 
    - *O(1) time for initialization.*
    - *O(n) time for each push() function call.*
    - *O(1) time for each pop() function call.*

- **💾 Space:** O(n)  
*Used queues of size n*
