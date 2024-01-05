```python
# Definition for singly-linked list.
from typing import Optional

class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        remains = 0

        prev = ListNode()
        head_prev = prev
        p1 = l1
        p2 = l2

        while p1 or p2:
            val1 = p1.val if p1 else 0
            val2 = p2.val if p2 else 0
            sum_value = val1 + val2 + remains
            if sum_value > 9:
                remains = 1
                sum_value -= 10
            else:
                remains = 0

            node = ListNode(val=sum_value)
            prev.next = node
            prev = node

        return head_prev.next

Бесконечный цикл. Забыл двигать p1 и p2
```

```python
# Definition for singly-linked list.
from typing import Optional

class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        remains = 0

        prev = ListNode()
        head_prev = prev
        p1 = l1
        p2 = l2

        while p1 or p2:
            val1 = p1.val if p1 else 0
            val2 = p2.val if p2 else 0
            sum_value = val1 + val2 + remains
            if sum_value > 9:
                remains = 1
                sum_value -= 10
            else:
                remains = 0

            node = ListNode(val=sum_value)
            prev.next = node
            prev = node
            p1 = p1.next
            p2 = p2.next

        return head_prev.next

AttributeError: 'NoneType' object has no attribute 'next'
     ^^^^^^^
p2 = p2.next

Не обработал значения None в p1 p2
```

```python
# Definition for singly-linked list.
from typing import Optional

class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        remains = 0

        prev = ListNode()
        head_prev = prev
        p1 = l1
        p2 = l2

        while p1 or p2:
            val1 = p1.val if p1 else 0
            val2 = p2.val if p2 else 0
            sum_value = val1 + val2 + remains
            if sum_value > 9:
                remains = 1
                sum_value -= 10
            else:
                remains = 0

            node = ListNode(val=sum_value)
            prev.next = node
            prev = node
            p1 = p1.next
            p2 = p2.next

        return head_prev.next

Цикл должен продолжить работу, если remains > 0

while p1 or p2 or remains
```