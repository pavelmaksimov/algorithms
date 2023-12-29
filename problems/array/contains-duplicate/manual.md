# [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)
Проверить, что массив содержит дубликаты.

Решение 1:
- Создать уникальное множество чисел входящего массива
- Сравнить кол-во
```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        return len(nums) != len(set(nums))
```
Оценка: `Time O(n), Mem O(n)`

Решение 2:
1. Создать множество
2. Запустить цикл по массиву
3. Проверять, есть ли число в множестве
4. Добавлять числа в множество
```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        container = set()
        for n in nums:
            if n in container:
                return True
            
            container.add(n)

        return False
```
Оценка: `Time O(n), Mem O(n)` в лучшем случае, когда дубликаты в начале стоят `Time O(1), Mem O(1)`

Решение 3:
1. Отсортировать входящий массив
2. Создать указатели на текущий и предыдущий
3. Сравнивать числа под указателями
4. Если одинаковые, то нашли дубликат
Оценка: `Time O(n log n), Mem O(1)`. При условии, что сортировка пирамидальная (Heap Sort)
