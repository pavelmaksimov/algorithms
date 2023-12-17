```python
class Solution:
    def isMonotonic(self, nums: List[int]) -> bool:
        is_decreasing = None
        is_increasing = None
        iprev = 0
        icurrent = 1
        while 1:
            try:
                current = nums[icurrent]
            except IndexError:
                break

            icurrent += 1

            if current > nums[iprev]:
                is_increasing = True
            elif current < nums[iprev]:
                is_decreasing = True
        
        if not is_decreasing and not is_increasing:
            return True
        elif is_decreasing and is_increasing:
            return False
        else:
            return True
Input
nums =
[1,3,2]
Output
true
Expected
false

iprev не увеличивал
```

```python
class Solution:
    def isMonotonic(self, nums: List[int]) -> bool:
        is_decreasing = None
        is_increasing = None
        iprev = 0
        icurrent = 1
        while 1:
            try:
                current = nums[icurrent]
            except IndexError:
                break

            icurrent += 1

            if current > nums[iprev]:
                is_increasing = True
            elif current < nums[iprev]:
                is_decreasing = True
        
        if is_decreasing is None and is_increasing is None:
            return True
        elif is_decreasing and is_increasing:
            return False
        else:
            return True
Input
nums =
[1,3,2]
Output
true
Expected
false

iprev не увеличивал
Не понял сразу, думал что в конце условия проверки флагов неверные. 
```

```python
class Solution:
    def isMonotonic(self, nums: List[int]) -> bool:
        is_decreasing = None
        is_increasing = None
        iprev = 0
        icurrent = 1
        while 1:
            try:
                current = nums[icurrent]
            except IndexError:
                break

            icurrent += 1
            iprev += 1

            if current > nums[iprev]:
                is_increasing = True
            elif current < nums[iprev]:
                is_decreasing = True
        
        if is_decreasing is None and is_increasing is None:
            return True
        elif is_decreasing and is_increasing:
            return False
        else:
            return True
Input
nums =
[1,3,2]
Output
true
Expected
false

рано увеличивал iprev, надо было после сравнения значений 
```