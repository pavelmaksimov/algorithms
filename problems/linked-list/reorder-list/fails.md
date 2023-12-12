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

```python

class Solution:
    def reorderList(self, head: Optional[ListNode]) -> None:
        """
        Do not return anything, modify head in-place instead.
        """
        dummy = ListNode(next=head)
        fast = dummy
        slow = dummy

        while fast and fast.next and fast.next.next:
            slow = slow.next
            fast = fast.next.next
        
        middle = slow.next
        current = middle
        slow.next = None
        prev = None

        while current:
            next = current.next
            current.next = prev
            prev = current
            current = next
        
        head2 = prev
        
        l = head
        r = head2

        while l:
            l_next = l.next
            r_next = r.next if r else None
            l.next = r
            if r:
                r.next = next
            l = l_next
            r = r_next
        
        return head
Input
head =
[1,2,3,4]
Output
[1,4]
Expected
[1,4,2,3]

head2 стоит на неверном узле, стоит на конце второй половины списка
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
        dummy = ListNode(next=head)
        fast = dummy
        slow = dummy

        while fast and fast.next and fast.next.next:
            slow = slow.next
            fast = fast.next.next
        
        middle = slow.next
        current = middle
        slow.next = None
        prev = None

        while current:
            next = current.next
            current.next = prev
            prev = current
            current = next
        
        head2 = middle
        
        l = head
        r = head2

        while l:
            l_next = l.next
            r_next = r.next if r else None
            l.next = r
            if r:
                r.next = next
            l = l_next
            r = r_next
        
        return head
Input
head =
[1,2,3,4]
Output
[1,3]
Expected
[1,4,2,3]

Неправильно на 3 этапе соединял узлы.
```