# [Bubble Sort](https://leetcode.com/problems/sort-an-array/submissions/1167889818/)

## Идея
Максимальный элементы по мере прохода по массиву будут, как бы всплывать наверх.
Попарно сравниваются элементы слева направо, двигается указатели, справа окажется максимальный и так n раз.
## Решение
```python
class Solution:
    def sortArray(self, nums: List[int]) -> List[int]:
        r = len(nums) - 1

        while r > 0:
            l = 0
            max_local = l
            while l <= r:
                if nums[l] > nums[max_local]:
                    max_local = l

                l += 1

            nums[r], nums[max_local] = nums[max_local], nums[r]
            r -= 1

        return nums
```
Оценка по памяти `O(1)`. Дополнительная память не используется.

Оценка по времени `O(n^2)`
