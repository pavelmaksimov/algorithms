# [Longest Continuous Increasing Subsequence](https://leetcode.com/problems/longest-continuous-increasing-subsequence/)
Дан неотсортированный массив. Вернуть размер подмассива с постоянно увеличивающейся последовательностью.
```
Input: nums = [1,3,5,4,7]
Output: 3 (1,3,5)

Input: nums = [2,2,3]
Output: 2 (2,3)

Input: nums = [2,2,2,2,2]
Output: 1
```
Идея:
Проходим по списку, сравниваем текущий элемент с максимальным. Если максимум меньше меньше, значит рост чисел прекратился.

Решение:
1. Заводим счетчик длины последовательности
2. Сохраняем предыдущее значение
3. Заводим максимум длин последовательностей
4. Идем по массиву, сравниваем текущий с предыдущим
5. Если текущий больше, значит последовательность увеличивается
6. Увеличиваем счетчик длины на 1
7. Обновляем максимум длин последовательностей
```python
class Solution:
    def findLengthOfLCIS(self, nums: List[int]) -> int:
        max_length = 1
        current_length = 0
        prev_element = 0
        for n in nums:
            if n > prev_element:
                current_length += 1
            else:
                current_length = 1
                
            max_length = max(max_length, current_length)
            prev_element = n

        return max_length
```
Оценка сложности по времени O(n)

Оценка сложности по памяти O(1)