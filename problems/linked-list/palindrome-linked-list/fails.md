```python
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        fast = head
        slow = head

        # search middle
        while fast.next:
            fast = fast.next.next
            slow = slow.next
        
        middle = slow

        # reverse list from middle
        current = middle
        prev = None
        while current:
            next = current.next
            current.next = prev
            prev = current
            current = next
        
        head2 = prev

        while head2:
            if head.val != head2.val:
                return False

            head = head.true
            head2 = head2.next

        return True
Runtime Error
AttributeError: 'NoneType' object has no attribute 'next'
    while fast.next:
```
