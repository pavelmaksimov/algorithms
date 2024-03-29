# [# Intersection Of Sorted Arrays](https://www.interviewbit.com/problems/intersection-of-sorted-arrays/)
## Задача
Найдите пересечение двух **отсортированных** массивов **ИЛИ** другими словами, учитывая 2 отсортированных массива, найдите все элементы, которые встречаются в обоих массивах.
```
1 <= |A| <= 106
1 <= |B| <= 106

Ввод 1:
A : [1 2 3 3 4 5 6]
B: [3 3 5]
Результат 1: [3 3 5]

Ввод 2:
A : [1 2 3 3 4 5 6]
B: [3 5]
Результат 1: [3 5]
```
## Идея
Использовать 2 указателя. Если значения равны, подвинуть оба. Если нет, то двигать тот, у которого значение меньше.
## Нюансы
## Решение
```python
def intersect(A, B):  
    l, r = 0, 0  
    result = []  
  
    while l < len(A) and r < len(B):  
        if A[l] == B[r]:  
            result.append(A[l])  
            l += 1  
            r += 1  
        elif A[l] < B[r]:  
            l += 1  
        else:  
            r += 1  
  
    return result
```
Оценка по памяти `O(n+m)`

Оценка по времени `O(n+m)`
