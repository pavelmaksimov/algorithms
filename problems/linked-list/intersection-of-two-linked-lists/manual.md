https://leetcode.com/problems/intersection-of-two-linked-lists/
Не оптимальное решение
```python
class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> Optional[ListNode]:
        # Разворачиваем первый список, O(n)
        prev = None
        current = headA

        while current:
            next = current.next
            current.next = prev
            prev = current
            current = next
        
        # Если списки пересекаются, указатель достигнет начало первого списка, O(n)
        is_intersect = False
        pointer = headB
        while pointer:
            if pointer == headA:
                is_intersect = True
                break
            
            pointer = pointer.next

        # Разворачиваем первый список в изначальное состояние, O(n)
        current = prev
        prev = None
        while current:
            next = current.next
            current.next = prev
            prev = current
            current = next
        
        if not is_intersect:
            return 

        # O(n * m)
        # Ставим указатель на первый список и двигаем его.
        pointer_a = headA
        while pointer_a:
            pointer_b = headB

            # Двигаем указатель по второму списку, ловим момент когда указатели встретятся, это будет нужный узел
            while pointer_b:
                if pointer_a == pointer_b:
                    return pointer_a

                pointer_b = pointer_b.next

            pointer_a = pointer_a.next
```
Оценка по скорости O(n * m), где n первый список, а m второй список.

Оценка по памяти O(1), память новых объектов постоянна, 
не зависит от длины списка.

Решение:

Разворачиваем первый список.
Далее перебираем второй список, если он дойдет до головы первого, значит списки пересекаются.
Разворачиваем в изначальной положение первый список.
Начинаем в цикле двигать указатель по первому списку. 
В этом цикле, запускаем цикл прохода указателя по второму списку и ждем  встречи указателей на узле, 
когда это произойдет, мы нашли узел пересечения.

