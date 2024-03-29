# [Valid Perfect Square](https://leetcode.com/problems/valid-perfect-square/)
## Задача
Учитывая положительное целое число, верните значение, `true` _если_ `num` _это идеальный квадрат или_ `false` _иначе_.

**Идеальный квадрат** - это целое число, равное квадрату целого числа. Другими словами, это произведение некоторого целого числа на себя.
```
Пример 1:

Ввод: число = 16 
Вывод:true 
Объяснение: Мы возвращаем true, потому что 4 * 4 = 16, а 4 - целое число.

Пример 2:
Ввод: число = 14 
Вывод:false 
Объяснение: Мы возвращаем false, потому что 3.742 * 3.742 = 14, а 3.742 не является целым числом.
```
## Идея
## Нюансы
## Решение
```python
class Solution:
    def isPerfectSquare(self, num: int) -> bool:
        l, r = 0, num + 1

        check = lambda m: m * m <= num

        while r - l > 1:
            mid = (l + r) // 2

            if check(mid):
                l = mid
            else:
                r = mid
            
        return l * l == num
```
Оценка по памяти `O(1)`

Оценка по времени `O(log n)`
