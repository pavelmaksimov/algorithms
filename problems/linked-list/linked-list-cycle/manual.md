```python

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        fast = head
        slow = head

        while fast and fast.next:
            
            if fast.next == slow:
                return True
        
            fast = fast.next.next
            slow = slow.next

            if fast == slow:
                return True
        
        return False
```
Оценка по скорости O(n), минимум мы пройдем в цикле весь список один раз, 
в худшем случае меньше, чем 2n.

Оценка по памяти O(1), память новых объектов постоянна, 
не зависит от длины списка.

Решение:

Применить паттерн быстрый и медленный указатели. 
Идея в том, что если список зациклен, 
то рано или поздно быстрый указатель догонит медленный.
