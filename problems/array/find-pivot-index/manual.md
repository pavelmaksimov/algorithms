https://leetcode.com/problems/find-pivot-index/

```python
from itertools import chain, accumulate

class Solution:
    def pivotIndex(self, nums: List[int]) -> int:
        accumulate_sum_list = list(accumulate(chain([0], nums)))
        full_summ = accumulate_sum_list[-1]

        pointer = 0
        end = len(nums) - 1

        while pointer <= end:
            accumulate_sum = accumulate_sum_list[pointer]
            current_num = nums[pointer]

            if full_summ - current_num - accumulate_sum == accumulate_sum:
                return pointer

            pointer += 1
        
        return -1
```
Оценка по скорости O(n), кол-во операций прямо зависит от кол-во элементов в списке.

Оценка по памяти O(n), за счет создания префиксного списка.

Решение:
- Считаем сумму элементов. 
- Создаем префиксный массив сумм с накоплением, начиная с 0
- Далее указателем проходим по элементам входящего массива
- Указателем проходим по входящему списку.
- Индекс указателя будет указывать в префиксном списке на сумму элементов до указателя
- По формуле проверяем, равны ли элементы слева и справа \
  (full_sum - accumulate - current_num == accumulate)

Нюансы:
- Указатель должен доходить в пределе до последнего элемента, включительно!
