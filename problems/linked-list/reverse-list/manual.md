# Reverse Linked List
```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        prev = None
        current = head

        while current:
            next = current.next
            current.next = prev
            prev = current
            current = next

        return prev
```

Оценка по времени O(n) потому что прохождение по всем элементам один раз

Оценка по памяти O(1), память объектов постоянная.

Решение:

Нужно перенаправить связь элемента со следующего на обратный элемент 
(для первого на None) и поменять местами предыдущий на текущий, 
далее повторять, пока элемент не будет None.
