# [Add Two Numbers](https://leetcode.com/problems/add-two-numbers/description/)

## Задача
Даны 2 односвязных списка. Вернуть односвязный список суммы их чисел.
```
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.

Example 2:
Input: l1 = [0], l2 = [0]
Output: [0]
```

## Решение
- Ставим указатели на входящие массивы
- Создаем переменную десятков, если сумма сложением будет больше 9, то десяток надо запоминать
- Создать фейковый узел, с которого будет начинаться новый список, его голову вернуть в конце надо
- В цикле складываем числа узлов
- Если полученное число больше 9, запоминаем его в переменной
- Число добавляем в новый список, как это сделать?
- Узел сохраняем в переменной prev, на следующем узле проставить ссылку prev.next=current, а prev=current
- При следующей итерации складываем числа и переменную десятков
- Учесть что списки могут быть разной длины
- Возвращаем голову нового списка
- 
## Нюансы
- Не забыть двигать узлы при переборе списков
- Когда двигаем узлы на следующий, учесть, что они могут быть уже None
- Цикл должен отработать, если узлы закончились, а остаток десятков больше 0
- Обработать сложение чисел узлов, когда узлов нету
- Нужно связывать узлы и заменять prev на current

```python
from typing import Optional

class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def addTwoNumbers(
            self, 
            l1: Optional[ListNode], 
            l2: Optional[ListNode]
    ) -> Optional[ListNode]:
        remains = 0

        prev = ListNode()
        head_prev = prev

        while l1 or l2 or remains:
            val1 = l1.val if l1 else 0
            val2 = l2.val if l2 else 0
            
            sum_value = val1 + val2 + remains
            remains = sum_value // 10

            node = ListNode(val=sum_value % 10)
            prev.next = node
            prev = node
            l1 = l1.next if l1 else None
            l2 = l2.next if l2 else None

        return head_prev.next
```
Оценка по памяти `O(n)`, один проход по списку максимальной длины

Оценка по времени `O(n)`, новый узел будет равен длине входящего списка, плюс один элемент в худшем случае.