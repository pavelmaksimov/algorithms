# [Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/description/)

## Задача
На горизонте расположены воздушные шары. Есть точки их начала и конца. Определить минимум выстрелов, чтобы их всех сбить.
```
Input: points = [[10,16],[2,8],[1,6],[7,12]]
Output: 2

Input: points = [[1,2],[3,4],[5,6],[7,8]]
Output: 4

Constraints:

1 <= points.length <= 105
points[i].length == 2
-231 <= xstart < xend <= 231 - 1
```
## Идея
Пытаться объединить интервалы. Если это возможно, значит их можно сбить одни выстрелом. Надо уменьшить интервал до интервала пересечения.

## Решение
- Отсортировать массив по начальным точкам
- Создать счетчик интервалов, которые не пересекаются
- В значение 1 т.к. начинаем проверять со второго интервала и один выстрел это минимум, чтобы сбить первый шарик
- Запомнить последний интервал пересечения в переменной, в начале это первый интервал
- Начинаем цикл со второго элемента
- В цикле сравнивать текущий и предыдущий интервалы
-  Если начало текущего меньше или равно концу предыдущему, значит они пересекаются
- Если интервалы пересекаются, то уменьшить интервал до точек интервала пересечения
- Если нет, то увеличить счетчик не пересекаемых интервалов и заменить последний интервал до текущего, далее надо сравнивать интервалы уже с ним

```python
class Solution:
    def findMinArrowShots(self, points: List[List[int]]) -> int:
        points.sort(key=lambda x: x[0])
        counter = 1
        last_points = points[0]

        for i in range(1, len(points)):
            current = points[i]
            
            if current[0] > last_points[1]:
                # Не пересекаются, увеличиваем счетчик и обновляем интервал
                counter += 1
                last_points = current
            else:
                # Пересекаются, поэтому уменьшаем интервал до точек пересечения.
                last_points[0] = max(last_points[0], current[0])
                last_points[1] = min(last_points[1], current[1])

        return counter
```

Оценка по памяти `O(n)`, из-за сортировки, без неё `O(1)`, т.к. память постоянна, не расчет от кол-во интервалов.
  
Оценка по времени `O(n log n)` из-за сортировки, без неё `O(n)`.
