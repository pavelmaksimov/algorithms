https://leetcode.com/problems/reorder-list/description/

```python
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

```

Оценка по скорости

Оценка по памяти O(1), память новых обхектов постоянная, 
не увеличивается от размера массива.

Решение:
Поставить указатель на PREV на фековый узел
Далее развернуть список со HEAD узла. Сохранять предыдущий узел PREV.
Дойдя до конца указать, PREV будет указывать на последний узел, 
сместить голову на него HEAD=PREV.
Не ясно, как разорвать связь первого и второго узла, 
чтоб при следующем цикле он не вернулся в предыдущую голову, иначе бесконечный цикл.
Т.к. как список развернут, повторить последовательность, начав с последнего узла, 
на котором стоит указатель PREV.
