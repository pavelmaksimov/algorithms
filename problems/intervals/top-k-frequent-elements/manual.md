# [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/description/)

## Задача
Учитывая целочисленный массив nums и целое число k, верните k наиболее часто встречающихся элементов. Вы можете вернуть ответ в любом порядке.
```
Example 1:
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]

Example 2:
Input: nums = [1], k = 1
Output: [1]

Constraints:
1 <= nums.length <= 105
-104 <= nums[i] <= 104
k is in the range [1, the number of unique elements in the array].
It is guaranteed that the answer is unique.
```
## Решение
- Создать массив массивов равный длине входящего массива + 1, чтобы могло поместиться макс. число в массиве
- Создаем словарь значение и его кол-во
- Проходимся по словарю
- Берем в качестве индекса, кол-во элементов и ставим под этим индексом в новом массиве значение, точнее добавляем в массив под этим индексом
- Проходимся с конца массива и берем нужное кол-во значений k

Оптимальное решение по времени
Оценка по памяти `O(n)`, размер счетчика и массива, зависит от n
Оценка по времени `O(n)`, создание счетчика и массива и поиск k, все это зависит от n
```python
from collections import Counter

class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        values = [[] for _ in range(len(nums) + 1)]

        for n, count in Counter(nums).items():
            values[count].append(n)

        result = [0] * k
        for n_list in reversed(values):
            for n in n_list:
                if k <= 0:
                    return result
                result[k-1] = n
                k -= 1

        return result
```

Не оптимальное решение, но памяти может использовать меньше.

Оценка по памяти `O(n)`, размер счетчика и массива, зависит от n, плюс для сортировки тоже `O(n)`
Оценка по времени `O(n log n)`, из-за сортировки плюс создание счетчика и массива
```python
from collections import defaultdict

class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        counter = defaultdict(lambda: 0)
        for n in nums:
            counter[n] += 1
        
        counter_array = sorted(((k, count) for k, count in counter.items()), key=lambda x: x[1], reverse=True)

        return [i[0] for i in counter_array[:k]]
```