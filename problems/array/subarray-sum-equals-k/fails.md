```python
from collections import defaultdict


class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        value_map = defaultdict(lambda: 0)
        value_map[0] += 1
        count = 0
        accumulate_sum = 0
        for n in nums:
            accumulate_sum += n
            count_nums = value_map.get(accumulate_sum - k, 0)
            count += count_nums
            value_map[n] += 1


Не вернул результат count
Смотреть внимательно перед отправкой, 
что должна вернуть функция и сравнивать с кодом.
```

```python
from collections import defaultdict

class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        value_map = defaultdict(lambda: 0)
        value_map[0] += 1
        count = 0
        accumulate_sum = 0
        for n in nums:
            accumulate_sum += n
            count_nums = value_map.get(accumulate_sum - k, 0)
            count += count_nums
            value_map[n] += 1

        return count

Неправильно понял решение
в value_map[n] += 1 надо сохранять value_map[accumulate_sum] += 1
```