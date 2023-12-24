# [Next Greater Node In Linked List](https://leetcode.com/problems/next-greater-node-in-linked-list/)
Задача:\
Найти следующий большой узел. Вернуть массив из значений больших узлов, стоящие за текущим. 
Поставить значение 0 если впереди нет значений больше.

```
Example 2:
Input: head = [2,7,4,3,5]
Output: [7,0,5,5,0]
```
Идея:\
Использовать стек. Надо развернуть список. Используя стек находим следующие большее число. Удаляем те, что меньше текущего.

Последовательность:
1. Разворачиваем список
2. Создаем стек
3. Проходим по списку
4. Вынимаем значение из стека до тех пор пока не встретили значение больше
5. Если больше, то берем большее значение и заносим в результат и обратно в стек
7. Добавляем текущее значение в стек
8. Разворачиваем массив и возвращаем

Нюансы:
- В конце надо развернуть массив
- Если нашли максимум, надо вернуть его в стек

# Решение
```python
from collections import deque

# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def nextLargerNodes(self, head: Optional[ListNode]) -> List[int]:
        # Разворачиваем список.
        length = 0
        prev = None
        current = head
        while current:
            next = current.next
            current.next = prev
            prev = current
            current = next
            length += 1
            
        # Ход с конца в начало теперь.
        result = [0] * length # Лучше сразу создать массив нужной длины
        stack = deque()
        i = 0
        current = prev
        while current:
            while stack:
                maxx = stack.pop()
                if current.val < maxx:
                    result[i] = maxx
                    stack.append(maxx)
                    break
            
            stack.append(current.val)
            current = current.next
            i += 1
        
        result.reverse()
        
        return result
```

# Сложность по скорости
O(n), кол-во операция прямо пропорционально зависит от кол-ва элементов в списке

# Сложность по памяти
O(n), В худшем случае, когда список отсортирован, в стек будут помещены все числа списка.
