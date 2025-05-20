## **LeetCode Link:** [#1700](https://leetcode.com/problems/number-of-students-unable-to-eat-lunch/)

## **Description**

You're given two lists:

- `students`: a queue of students, each with a preference for a type of sandwich (`0` or `1`).
    
- `sandwiches`: a stack of sandwiches, each of type `0` or `1`.
    

The rule is:

- If the student at the front of the queue wants the sandwich at the top of the stack, they take it and both are removed.
    
- If not, the student goes to the back of the queue.
    

The goal is to **return the number of students who cannot eat** (because the remaining students only want one type of sandwich, and the top sandwich is the other type).

## **Solution**
```python
from collections import deque

class Solution:
    def countStudents(self, students: List[int], sandwiches: List[int]) -> int:
        students = deque(students)
        sandwiches = deque(sandwiches)

        rotations = 0
        
        while students and rotations < len(students):
            if students[0] == sandwiches[0]:
                students.popleft()
                sandwiches.popleft()
                rotations = 0  # Reset because we made progress
            else:
                students.append(students.popleft())
                rotations += 1  # No one took sandwich, so count rotation
        
        return len(students)
```

### **Complexity:**
- **⚡ Time:** O(n^2)  
*Rotation could be twice if everyone rotates*  

- **💾 Space:** O(n)  
*Used queue variables*
