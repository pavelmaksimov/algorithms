# [Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)
## Задача
Учитывая **1-индексированный** массив целых чисел, неубывающей последовательности `numbers`, найдите два числа так, чтобы в сумме они составляли определенное `target` число. Пусть эти два числа будут `numbers[index1]` и `numbers[index2]` где `1 <= index1 < index2 <= numbers.length`.

Возвращает _индексы двух чисел,_ `index1` _и_ `index2`_, **добавленные на единицу** в виде целого массива_ `[index1, index2]` _длиной 2._

Тесты генерируются таким образом, что существует **ровно одно решение**. Вы **не можете** использовать один и тот же элемент дважды.

Ваше решение должно использовать только постоянное дополнительное пространство.
```
Пример 1:
Входные данные: числа = [2,7, 11,15], target = 9 
Вывод: [1,2]
Объяснение: Сумма 2 и 7 равна 9. Следовательно, индекс1 = 1, индекс2 = 2. Возвращаем [1, 2].

Пример 2:
Входные данные: числа = [2, 3, 4], цель = 6 
Вывод: [1,3]
Объяснение: Сумма 2 и 4 равна 6. Следовательно, индекс1 = 1, индекс2 = 3. Возвращаем [1, 3].

Пример 3:
Входные данные: числа = [-1,0], цель = -1 
Вывод: [1,2]
Объяснение: Сумма значений -1 и 0 равна -1. Следовательно, индекс1 = 1, индекс2 = 2. Возвращаем [1, 2].
```
## Идея
Использовать два указателя, в начале и в конце списка. Суммировать значения, если меньше целевого, то двигать левый указатель, иначе правый. Такое решение подходит т.к. последовательность не убывающая.
## Нюансы
## Решение
```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        l, r = 0, len(numbers) - 1

        while l < r:
            value = numbers[l] + numbers[r]

            if value == target:
                break

            if value < target:
                l += 1
            else:
                r -= 1
        
        return [l+1, r+1]
```
Оценка по памяти `O(1)`

Оценка по времени `O(n)`
