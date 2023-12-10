```python
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:

        dummy = ListNode(next=head)

        fast = dummy
        slow = dummy

        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next

        return slow

Output
[3,4,5,6]
Expected
[4,5,6]
```

```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:

        dummy = ListNode(next=head)

        fast = dummy
        slow = dummy

        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next

            if not fast.next:
                slow = slow.next

        return slow

AttributeError: 'NoneType' object has no attribute 'next'
    if not fast.next:
```