https://leetcode.com/problems/merge-k-sorted-lists/

```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def getMinimalNode(self, heads):
        """
        time O(k), где k число списков.
        """
        min_value = float('inf')
        min_node = None
        min_index = None

        for i in range(len(heads)):
            head = heads[i]
            if head and head.val < min_value:
                min_node = head
                min_value = head.val
                min_index = i

        if min_node:
            heads[min_index] = min_node.next
        
        return min_node

    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        dummy = ListNode()
        tail = dummy
        
        while 1:
            min_node = self.getMinimalNode(lists)
            if not min_node:
                return dummy.next

            tail.next = min_node
            tail = min_node
```

Оценка по скорости O(k*n), 
где O(k) скорость нахождения минимального значения у списков. 
И O(n) скорость построения нового отсортированного списка.

Оценка по памяти O(1), память новых обхектов постоянная, 
не увеличивается от размера массива.

Решение:
Добавляем фейковый узел. 
Ддалее находим ноду с минимальынм значением из списка голов списков. 
У этого списка сдвигаем голову на следующий узел. 
Предыдущий найденный узел цепляем к найдему минимальному. 
