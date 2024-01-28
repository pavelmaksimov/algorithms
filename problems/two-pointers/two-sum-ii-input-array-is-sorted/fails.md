```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        l, r = 0, len(numbers) - 1

        while l < r:
            value = numbers[l] + numbers[r]

            if value == target:
                break

            if value < target:
                l += 1
            else:
                r -= 1
        
        return [l, r]
        
В ТЗ сказано, что нужно вернуть индексы позиций значений, начиная с 1, т.е. индексирование начинается с 1
[l+1, r+1]
```