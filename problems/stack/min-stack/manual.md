# [Min Stack](https://leetcode.com/problems/min-stack/description/)

## Задача
Создайте стек, который поддерживает push, pop, top и получение минимального элемента за постоянное время.

Реализации MinStack класс:
- MinStack() инициализирует объект стека.
- void push(int val) помещает элемент val в стек.
- void pop() удаляет элемент, находящийся в верхней части стека.
- int top() получает верхний элемент стека.
- int getMin() извлекает минимальный элемент в стеке.
- Вы должны реализовать решение с O(1) временной сложностью для каждой функции.

```
Ввод
["minStack", "push", "push", "push", "getMin", "pop", "top", "getMin"]
[[],[-2],[0],[-3],[],[],[],[]]

Вывод
[null, null, null, null, -3, null, 0,-2]

Объяснение
minStack minStack = новый minStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin(); // возвращает -3 
minStack.pop();
minStack.top(); // возвращает 0 
minStack.getMin(); // возвращает -2
```
## Идея
Использовать два стека, в одном хранить значения, в другом минимальные значения. Тога можно для функции getMin добиться временной сложности `O(1)`
## Нюансы
1. Проверять, что стек не пустой
2. Добавлять значения в стек минимальных значений, !даже если значение равно последнему минимуму
## Решение
```python
class MinStack:
    def __init__(self):
        self.stack = []
        self.min_stack = []
        
    def push(self, val: int) -> None:
        self.stack.append(val)
        if not self.min_stack or val <= self.min_stack[-1]:
            self.min_stack.append(val)

    def pop(self) -> None:
        if self.stack:
            val = self.stack.pop()
            
            if self.min_stack and self.min_stack[-1] == val:
                self.min_stack.pop()

    def top(self) -> int:
        if self.stack:
            return self.stack[-1]

    def getMin(self) -> int:
        if self.min_stack:
            return self.min_stack[-1]
```