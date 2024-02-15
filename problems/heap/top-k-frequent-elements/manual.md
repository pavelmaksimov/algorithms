# [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)
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
Самое быстрое решение использовать кучу.
```python
import heapq
from collections import Counter

class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        counter = [(-c, n) for n, c in Counter(nums).items()]
        heapq.heapify(counter)
        return [heapq.heappop(counter)[1] for _ in range(k)]
```
Оценка по памяти: выделяется для подсчета кол-ва элементов, это `O(n)`.

Оценка по времени: создание кучи это `O(n)`, извлечение минимума `O(k * log n)`, итого `O(n + (k * log n))`.