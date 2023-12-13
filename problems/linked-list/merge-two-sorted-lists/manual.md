https://leetcode.com/problems/merge-two-sorted-lists/

```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
        
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        left = list1
        right = list2
        dummy = ListNode(next=list1)
        tail = dummy
        
        while left or right:
            if not right or (left and left.val <= right.val):
                next = left.next
                tail.next = left
                tail = left
                left = next
            else:
                next = right.next
                tail.next = right
                tail = right
                right = next

        return dummy.next
```
Оценка по скорости O(n), один цикл по всем элементам.

Оценка по памяти O(1), память новых объектов постоянна, 
не зависит от длины списка.

Решение:

Добавляем фейковый узел и ставим на него указатель TAIL. 
Также ставим указатели на оба списка. 
Далее берем узел с минимальным значением из двух списков и цепляем к нему хвост TAIL,
смещая указатель списка из которого взяли элемент.
