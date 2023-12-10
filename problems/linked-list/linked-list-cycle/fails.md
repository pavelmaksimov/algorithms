```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, x=None, next=None):
        self.val = x
        self.next = next

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        dummy = ListNode(next=head)

        fast = dummy
        slow = dummy

        while fast.next:
            fast = fast.next.next
            slow = slow.next

            if fast == slow or fast.next == slow:
                return True
        
        return False

AttributeError: 'NoneType' object has no attribute 'next'  
    if fast == slow or fast.next == slow:
```

```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, x=None, next=None):
        self.val = x
        self.next = next

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        dummy = ListNode(next=head)

        fast = dummy
        slow = dummy

        while fast.next:
            
            if fast == slow or fast.next == slow:
                return True
        
            fast = fast.next.next
            slow = slow.next

        return False

```

```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, x=None, next=None):
        self.val = x
        self.next = next

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        dummy = ListNode(next=head)

        fast = dummy
        slow = dummy

        while fast.next:
            
            if fast.next == slow:
                return True
        
            fast = fast.next.next
            slow = slow.next

            if fast == slow:
                return True
        
        return False
AttributeError: 'NoneType' object has no attribute 'next'
    while fast.next:
```