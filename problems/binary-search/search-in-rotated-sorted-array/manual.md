# [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)
## Задача
Вам будет предоставлена `m x n` целочисленная матрица `matrix` со следующими двумя свойствами:

- Каждая строка сортируется в неубывающем порядке.
- Первое целое число каждой строки больше последнего целого числа предыдущей строки.

По заданному целому числу `target` верните значение, `true` _если_ `target` _находится в_ `matrix` _или_ `false` _иначе_.

Вы должны написать решение с `O(log(m * n))` временной сложностью.
```
Ввод: матрица = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3 
Вывод: true

Ввод: матрица = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13 
Вывод: false
```
## Идея
Использовать два поиска. Сначала по начальным элементам массивов, чтобы определить, в каком искать вторым поиском. Потом вторым поиском элемент в массиве.
## Нюансы
- Во втором поиске, правый указатель ставить от длины массива, а не матрицы!
- Сравнение тоже производить указывая индекс найденный из первого поиска и второго
## Решение
```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        check = lambda m: matrix[m][0] <= target

        l, r = 0, len(matrix)

        while r - l > 1:
            mid = (l + r) // 2

            if check(mid):
                l = mid
            else:
                r = mid

        mi = l
        check = lambda m: matrix[mi][m] <= target

        l, r = 0, len(matrix[mi])

        while r - l > 1:
            mid = (l + r) // 2

            if check(mid):
                l = mid
            else:
                r = mid
        
        return target == matrix[mi][l]
```
Оценка по памяти `O(1)`

Оценка по времени `O(log(n) + log(m)) = O(log(n*m))`

## Решение 2
Один поиск. Работа, как с одним массивом.
```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        # чтобы работать с 2-D массивом как с 1-D
        def elementFromMatrix(i: int):
            n = len(matrix[0])
            return matrix[i // n][i % n]

        def good(i: int):
            return elementFromMatrix(i) <= target
        
        # обычный бинарный поиск как для 1-D массива
        l, r = 0, len(matrix) * len(matrix[0])
        while r - l > 1:
            m = (l + r) // 2
            if good(m):
                l = m
            else:
                r = m
                
        return elementFromMatrix(l) == target
```
