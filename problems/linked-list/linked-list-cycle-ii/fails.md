```python
class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        prev = head
        fast = head
        slow = head

        while fast and fast.next:
            prev = fast
            fast = fast.next.next
            slow = slow.next

            if fast == slow:
                return prev
Ввод
[-21,10,17,8,4,26,5,35,33,-7,-16,27,-12,6,29,-12,5,9,20,14,14,2,13,-24,21,23,-21,5]
24
Вывод
хвост подключается к узлу с индексом 26
Ожидается
хвост подключается к индексу узла 24
```