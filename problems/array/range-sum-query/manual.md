https://leetcode.com/problems/range-sum-query-immutable/submissions/1124438334/

```python
from itertools import chain, accumulate


class NumArray:
    def __init__(self, nums):
        self.accumulate_nums = self._accumulate(nums)

    def _accumulate(self, nums):
        return list(accumulate(chain([0], nums)))

    def sumRange(self, left: int, right: int) -> int:
        return self.accumulate_nums[right+1] - self.accumulate_nums[left]
```
## Оценка

Для NumArray.sumRange оценка по скорости и памяти O(1)

Для NumArray._accumulate оценка по скорости и памяти O(1)

В целом получается амортизационная оценка по скорости и памяти O(1).

## Решение

Создаем дополнительный массив суммы с накоплением. Добавляя 0 в начало, 
чтоб обработать исключительные случаи. 
Если вычесть из следующего элемента за правым краем подсчитываемого среза, 
элемент под указателем левого края, то мы получаем сумму этого среза.
