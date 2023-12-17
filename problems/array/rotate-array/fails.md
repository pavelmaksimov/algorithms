```python
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        l = 0
        r = -1
        while l < k:
            nums[l], nums[r] = nums[r], nums[l]
            l += 1
            r -= 1
        
        for i in range(1, len(nums) - k):
            nums[i], nums[i-1] = nums[i-1], nums[i]
        
        for i in range(k + 1, len(nums)):
            nums[i], nums[i-1] = nums[i-1], nums[i]
Input
nums = [1,2,3,4,5,6,7]
k = 3
Output
[6,5,4,3,2,1,7]
Expected
[5,6,7,1,2,3,4]        
```

```python
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        l = 0
        r = -1
        while l < k:
            nums[l], nums[r] = nums[r], nums[l]
            l += 1
            r -= 1
        
        for i in range(1, k):
            nums[i], nums[i-1] = nums[i-1], nums[i]
        
        for i in range(k + 1, len(nums)):
            nums[i], nums[i-1] = nums[i-1], nums[i]
Input
nums = [1,2,3,4,5,6,7]
k = 3
Output
[6,5,7,3,2,1,4]
Expected
[5,6,7,1,2,3,4]

Разворачивал неправильно, я переставлял последовательно, текущий элемент с предыдущим, 
а надо было переставлять крайние элементы.
Плюс тут элементы при последовательном разворачивании были неверные
вместо 
        for i in range(k + 1, len(nums)):
правильнее
        for i in range(k + 2, len(nums)):
```

```python
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        l = 0
        r = -1
        while l < k:
            nums[l], nums[r] = nums[r], nums[l]
            l += 1
            r -= 1
        
        l = 0
        r = k - 1
        while l < r:
            nums[l], nums[r] = nums[r], nums[l]
            l += 1
            r -= 1
        
        l = -k - 1
        r = -1
        while l < r:
            nums[l], nums[r] = nums[r], nums[l]
            l += 1
            r -= 1
Input
nums = [-1,-100,3,99]
k = 2
Output
[3,-1,-100,99]
Expected
[3,99,-1,-100]        
Последнее разворачивание списка кривое 
```

```python
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        l = 0
        r = -1
        while l < k:
            nums[l], nums[r] = nums[r], nums[l]
            l += 1
            r -= 1
        
        l = 0
        r = k - 1
        while l < r:
            nums[l], nums[r] = nums[r], nums[l]
            l += 1
            r -= 1
        
        l = k
        r = len(nums)
        while l < r:
            nums[l], nums[r] = nums[r], nums[l]
            l += 1
            r -= 1
Не вычел единицу из: 
r = len(nums)  
```

```python
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        l = 0
        r = -1
        while l < k:
            nums[l], nums[r] = nums[r], nums[l]
            l += 1
            r -= 1
        
        l = 0
        r = k - 1
        while l < r:
            nums[l], nums[r] = nums[r], nums[l]
            l += 1
            r -= 1
        
        l = k
        r = len(nums) - 1
        while l < r:
            nums[l], nums[r] = nums[r], nums[l]
            l += 1
            r -= 1
IndexError: list index out of range
Use Testcase
nums = [-1]
k = 2   

Не думал, что k может быть больше длины списка
```