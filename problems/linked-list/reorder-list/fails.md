```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
class Solution:
    def reorderList(self, head: Optional[ListNode]) -> None:
        """
        Do not return anything, modify head in-place instead.
        """
        prev = None # ListNode(next=head)
        current = head

        while prev != head:
            while current:
                next = current.next
                current.next = prev
                prev = current
                current = next

            head.next = prev
            head = prev
            current = prev.next
            prev = None
Time Limit Exceeded
```
```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
class Solution:
    def reorderList(self, head: Optional[ListNode]) -> None:
        """
        Do not return anything, modify head in-place instead.
        """
        h = head
        prev = None # ListNode(next=head)
        current = head

        while head and head.next:
            while current:
                next = current.next
                current.next = prev
                prev = current
                current = next

            head.next = prev
            head = prev
            current = prev
            prev.next = None
            prev = None

        return h
Input
head =
[1,2,3,4]
Output
[1,4]
Expected
[1,4,2,3]

Input
head =
[1,2,3,4,5]
Output
[1,5]
Expected
[1,5,2,4,3]
```

```python
class Solution:
    def reorderList(self, head: Optional[ListNode]) -> None:
        """
        Do not return anything, modify head in-place instead.
        """
        h = head
        prev = None
        current = head

        while current.next:
            while current:
                next = current.next
                current.next = prev
                prev = current
                
                if prev.next == head:
                    prev.next = None
                
                current = next

            head.next = prev
            head = prev
            current = prev
            prev = None

        return h
Time Limit Exceeded    

Проблема в том, что в зацикленных списках, этот алгоритм считает бесконечно.
```