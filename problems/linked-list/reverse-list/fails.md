```python
# Definition for singly-linked list.

class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        """O(n), O(1)"""

        if not head:
            return

        prev = None
        current = head

        while current:
            tmp = current
            current.next = prev
            prev = current
            current = tmp.next

        return prev

Output
[1]
Expected
[5,4,3,2,1]
```