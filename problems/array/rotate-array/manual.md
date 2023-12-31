```python
class Solution:
    def rotate_sub(self, nums, l, r):
        r -= 1
        while l < r:
            nums[l], nums[r] = nums[r], nums[l]
            l += 1
            r -= 1

    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        k = k % len(nums)
        self.rotate_sub(nums, 0, len(nums))
        self.rotate_sub(nums, 0, k)
        self.rotate_sub(nums, k, len(nums))
```
Оценка по скорости O(n), потому что кол-во сдвигов зависит от длины списка.

Оценка по памяти O(1), память постоянная, не увеличивается от кол-ва объектов.

Решение:

Ротация происходит так. На сначала переставить из конца в начало.
Далее переставить элементы по отдельности в двух срезах.

Из нюансов, k может быть больше длины массива. 
Типа по условию это кол-во раз, на которое идет сдвиг всех элементов вперед. 
Это означает, что если элементов в списке 2 и надо сдвинуть на 2, 
то это будет такой же список.

2 % len(1) = 0

Чтоб не двигать лишнего вычисляется новый k.
```python
k = k % len(nums)
```
