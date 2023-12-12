https://leetcode.com/problems/reorder-list/description/

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

        # Get pre middle element.
        fast = head
        slow = head

        while fast and fast.next and fast.next and fast.next.next:
            slow = slow.next
            fast = fast.next.next
        
        middle = slow.next
        current = middle
        slow.next = None
        prev = None

        # Reverse from middle element.
        while current:
            next = current.next
            current.next = prev
            prev = current
            current = next
        
        # New link for nodes.
        l = head
        r = prev

        while r:
            next = l.next
            l.next = r
            l = r
            r = next
        
        return head
```

Оценка по скорости O(n log n)

Оценка по памяти O(1), память новых обхектов постоянная, 
не увеличивается от размера массива.

Решение:
Найти центральны элемент (со смещением влево в четном списке)
Развернуть вторую половина списка (после премид элемента), после этого начало списка будет None. 
Следующий элемент конца первой половины указать на `None`, иначе будет зацикливание, бесконечный цикл.
Далее идем в цикле по двум спискам и переназначаем ссылки.
