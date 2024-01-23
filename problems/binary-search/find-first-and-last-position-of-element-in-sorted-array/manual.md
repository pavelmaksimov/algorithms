# [Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
## Задача
Учитывая массив целых чисел, `nums` отсортированных в неубывающем порядке, найдите начальную и конечную позиции данного `target` значения.

Если `target` не найден в массиве, верните `[-1, -1]`.
```
Пример 1:

Входные данные: nums = [5,7,7,8,8,10], target = 8 
Выходные данные: [3,4]

Пример 2:
Входные данные: nums = [5,7,7,8,8,10], target = 6 
Выходные данные: [-1,-1]

Пример 3:
Входные данные: nums = [], target = 0 
Выходные данные: [-1,-1]
```
## Идея
Использовать два поиска.
## Нюансы
- Обрабатывать крайний случай, когда приходит пустой массив
- После первого поиска проверять, что число есть в массиве, если нет завершить
## Решение
```python
class Solution:
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        result = []

        check = lambda m: nums[m] < target

        l, r = -1, len(nums) - 1

        while r - l > 1:
            mid = (l + r) // 2

            if check(mid):
                l = mid
            else:
                r = mid
        
        if not nums or nums[r] != target:
            return [-1, -1]

        result.append(r)

        check = lambda m: nums[m] <= target

        l, r = 0, len(nums)

        while r - l > 1:
            mid = (l + r) // 2

            if check(mid):
                l = mid
            else:
                r = mid

        result.append(l)

        return result

```
Оценка по памяти `O(1)`

Оценка по времени `O(log n)`
