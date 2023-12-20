```python
from itertools import chain, accumulate
from functools import reduce

class Solution:
    def pivotIndex(self, nums: List[int]) -> int:
        full_summ = reduce(lambda x, y: x+y, nums)
        accumulate_sum_list = list(accumulate(chain([0], nums)))

        pointer = 1
        end = len(nums) - 1

        while pointer < end:
            accumulate_sum = accumulate_sum_list[pointer - 1]
            current_num = accumulate_sum_list[pointer]

            if full_summ - accumulate_sum == current_num:
                return pointer

            pointer += 1
        
        return -1
    
при возврате ответа не уменьшил pointer на 1
Надо было: return pointer - 1

Вообще неправильеую формулу подобрал
```

```python
from itertools import chain, accumulate
from functools import reduce

class Solution:
    def pivotIndex(self, nums: List[int]) -> int:
        full_summ = reduce(lambda x, y: x+y, nums)
        accumulate_sum_list = list(accumulate(chain([0], nums)))

        pointer = 0
        end = len(nums) - 1

        while pointer < end:
            accumulate_sum = accumulate_sum_list[pointer]
            current_num = nums[pointer]

            if full_summ - current_num - accumulate_sum == accumulate_sum:
                return pointer

            pointer += 1
        
        return -1
Input nums = [-1,-1,0,1,1,0]
Output -1
Expected 5

Последний элемент не проверялся, надо было так сделать
while pointer <= end:
```