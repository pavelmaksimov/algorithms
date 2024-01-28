```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        this, target = 0, 0

        while target < len(nums):
            if nums[target] == 0:
                target += 1
            
            elif nums[this] == 0:
                nums[this], nums[target] = nums[target], nums[this]
                this += 1
                target += 1

        return nums
Бесконечный цикл, указатели не во всех случаях сдвигаются.        
```