https://leetcode.com/problems/monotonic-array/

```python
class Solution:
    def isMonotonic(self, nums: List[int]) -> bool:
        is_decreasing = True
        is_increasing = True
        
        for i in range(1, len(nums)):
            prev = nums[i-1]

            is_decreasing = is_decreasing and nums[i] <= prev
            is_increasing = is_increasing and nums[i] >= prev

        return is_decreasing or is_increasing
        
```
Оценка по скорости O(n), потому что один раз проходим по всему списку.

Оценка по памяти O(1), память постоянная, не увеличивается от кол-ва объектов.

Решение:
Проходим по циклу и сравниваем текущий элемент с предыдущим. 
Три варианта значений флага в конце цикла:
- Оба True, значит все элементы равны, что означает монотонный массив.
- Оба False, значит массив не монотонный.
- Один из флагов будет True, другой False, что означает монотонный массив.



То же самое, но сложнее.
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

            if current > nums[iprev]:
                is_increasing = True
            elif current < nums[iprev]:
                is_decreasing = True
        
            icurrent += 1
            iprev += 1

        if is_decreasing is None and is_increasing is None:
            return True
        elif is_decreasing and is_increasing:
            return False
        else:
            return True
```
