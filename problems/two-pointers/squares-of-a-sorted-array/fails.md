```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        l, r = 0, len(nums) - 1
        result = [None] * len(nums)
        current = 0

        while current < len(nums):
            if nums[l] * nums[l] <= nums[r] * nums[r]:
                result[current] = nums[l] * nums[l]
            else:
                result[current] = nums[r] * nums[r]
            
            current += 1

        return result

Забыл подвинуть указатели l и r.
```
```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        l, r = 0, len(nums) - 1
        result = [None] * len(nums)
        current = 0

        while current < len(nums):
            if nums[l] * nums[l] <= nums[r] * nums[r]:
                result[current] = nums[l] * nums[l]
                l += 1
            else:
                result[current] = nums[r] * nums[r]
                r += 1
            
            current += 1

        return result

Правый указатель надо двигать в обратную сторону.
r -= 1
```
```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        l, r = 0, len(nums) - 1
        result = [None] * len(nums)
        current = 0

        while current < len(nums):
            if nums[l] * nums[l] <= nums[r] * nums[r]:
                result[current] = nums[l] * nums[l]
                l += 1
            else:
                result[current] = nums[r] * nums[r]
                r -= 1
            
            current += 1

        return result
Надо заполнять массив с конца, искать в указателях самый большой элемент.
```
```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        l, r = 0, len(nums) - 1
        result = [None] * len(nums)
        current = len(nums) - 1

        while current >= 0:
            if nums[l] * nums[l] <= nums[r] * nums[r]:
                result[current] = nums[l] * nums[l]
                l += 1
            else:
                result[current] = nums[r] * nums[r]
                r -= 1
            
            current -= 1

        return result
    
Забыл изменить условие на поиск большего элемента
if nums[l] * nums[l] >= nums[r] * nums[r]:
```