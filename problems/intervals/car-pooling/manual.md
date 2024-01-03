# [Car Pooling](https://leetcode.com/problems/car-pooling/)

Есть автомобиль с количеством свободных мест. Движется только вперед. Выяснить, хватит ли его вместимости перевести всех пассажиров.

Решение:
1. Cтавим два указателя, оба будут указывать на массив, но на разные точки, посадки или высадки
2. Берем минимальное из них
3. Если из указателя на начальную точку, то вычитаем вместимость пассажиров
4. Если из указателя на конечную точку, прибавляем вместимость пассажиров
5. Проверяем на каждом шаге, что `capacity  > 0`

```python
class Solution:
    def carPooling(self, trips: List[List[int]], capacity: int) -> bool:
        trips.sort(key=lambda x: x[2])
        start = 0
        end = 0

        while start < len(trips) or end < len(trips):
            if start < len(trips) and trips[start][1] < trips[end][2]:
                capacity -= trips[start][0]
                start += 1
            else:
                capacity += trips[end][0]
                end += 1

            if capacity < 0:
                return False
        
        return True
```
Оценка по памяти O(n), из-за сортировки, без неё O(1)

Оценка по времени O(n log n) из-за сортировки, без неё O(n)