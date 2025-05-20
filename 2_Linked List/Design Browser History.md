## **LeetCode Link:** [#1472](https://leetcode.com/problems/design-browser-history/)

## **Solution**
```python
class ListNode:
    def __init__(self, val, prev=None, next=None):
        self.val = val
        self.prev = prev
        self.next = next

class BrowserHistory:

    def __init__(self, homepage: str):
        self.cur = ListNode(homepage)

    def visit(self, url: str) -> None:
        self.cur.next = ListNode(url, self.cur)
        self.cur = self.cur.next

    def back(self, steps: int) -> str:
        while self.cur.prev and steps > 0:
            self.cur = self.cur.prev
            steps -= 1
        return self.cur.val

    def forward(self, steps: int) -> str:
        while self.cur.next and steps > 0:
            self.cur = self.cur.next
            steps -= 1
        return self.cur.val
```

### **Complexity:**
- **⚡ Time:** 
- *O(1) time for initialization.*
- *O(1)O(1) time for each visit()visit() function call.*
- *O(min(n,steps))O(min(n,steps)) time for each back()back() and forward()forward() function calls.*

- **💾 Space:** O(m * n)  
*n is the number of visited urls, m is the average length of each url,*
