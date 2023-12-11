```python
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        fast = head
        slow = head

        # search middle
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next
        
        middle = slow

        # reverse list from middle
        current = middle
        prev = None
        while current:
            next = current.next
            current.next = prev
            prev = current
            current = next
        
        head2 = prev
        
        # check
        while head2:
            if head.val != head2.val:
                return False

            head = head.next
            head2 = head2.next

        return True
```

Оценка по скорости O(n)

Оценка по памяти O(1), память новых обхектов постоянная, 
не увеличивается от размера массива.

Решение:

Сначала нужно найти центр списка. 
Потом от центра списка развернуь список.
И в цикле проверить совпадение символов, двигая указатели по обоим спискам.
