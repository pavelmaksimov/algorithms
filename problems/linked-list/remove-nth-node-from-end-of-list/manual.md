# Удалить узел с конца

```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next


class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        dummy_node = ListNode(next=head)

        fast = dummy_node
        for i in range(n + 1):
            fast = fast.next
        
        low = dummy_node

        while fast:
            fast = fast.next
            low = low.next
        
        low.next = low.next.next

        return dummy_node.next
```

## Оценка по времени `O(n)`
Перебор элементов списка прямо зависит от размера списка.

## Оценка по памяти `O(1)`
Кол-во создаваемых объектов постоянное и не увеливается от размера списка. 

Также добавить Dymmy Node в начало списка, чтоб не приводило к исключительным случаям.

Добавить быстрый и медленный указатель (не паттерн)

## Описание
Если удаляем 2-ой элемент с конца, 
то сначала верхний быстрый указатель ставим на n+1, 
когда в цикле до него дошли, 
ставим указатель на первый пустой узел и сдвигаем оба, 
пока быстрый указатель не дойдет до NULL.
