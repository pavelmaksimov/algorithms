https://leetcode.com/problems/subarray-sum-equals-k/

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
            value_map[accumulate_sum] += 1

        return count
```
# Оценка по скорости O(n)
Потому что один раз проходим по всему списку.

# Оценка по памяти
O(n), память расходуется на словарь, размер его зависит от кол-ва объектов, 
в худшем случае там будет кол-во элементов равное входящему массиву.

# Решение:
https://youtu.be/fFVZt-6sgyo?si=PZfaBfsMR5w_zNri

1. Создаем словарь, в котором будут хранится {"сумма с накоплением": их кол-во}
2. Добавляем в него первую сумму 0, т.е словрь такой будет {0: 1}
3. Добавляем счетчик суммы с накоплением
4. Счетчик кол-ва подмассивов, сумма которых равное К
5. Проходим циклом по массиву
6. Увеличиваем сумму с накоплением
7. Смотрим есть ли в словаре подмассивы с суммой (accumulate_sum - k)
8. Увеличиваем счетчик найденных подмассивов на кол-во таких сумм в словаре 
   value_map.get(accumulate_sum - k, 0)
9. Добавляем текущую или увеличиваем уже сущуствующую сумму с накоплением в словаре
10. Возврашаем результат
