# [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)
## Задача
Учитывая строку,`s`содержащую только символы`'('`,`')'`,`'{'`,`'}'``'['`,`']'`. Определите, является ли введенная строка допустимой.

Входная строка допустима, если:

1. Открытые квадратные скобки должны быть закрыты скобками того же типа.
2. Открытые квадратные скобки должны быть закрыты в правильном порядке.
3. Каждой закрывающей скобке соответствует открывающая скобка того же типа.
```
Пример 1:

Ввод: s = "()"
Вывод: true
Пример 2:

Ввод: s = "()[]{}"
Вывод: true
Пример 3:

Ввод: s = "(]"
Вывод: false

Ограничения:

1 <= s.length <= 104
s состоит только из скобок '()[]{}'.
```
## Идея
Использовать стек
## Нюансы
## Решение
```python
from collections import deque

class Solution:
    def isValid(self, text: str) -> bool:
        spec = {'(': ')', '{': '}', '[': ']'}
        stack = deque()

        for s in text:
            if s in spec:
                stack.append(s)
                continue

            if not stack:
                return False
                    
            open_ = stack.pop()

            if s != spec[open_]:
                return False
                
        return len(stack) == 0
```
Оценка по памяти `O(n)`

Оценка по времени `O(n)`
