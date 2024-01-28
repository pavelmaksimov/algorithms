# [Move Zeroes](https://leetcode.com/problems/move-zeroes/)
## Задача
Учитывая массив целых чисел `nums`, переместите все `0` в конец его, сохраняя относительный порядок ненулевых элементов.

**Обратите** внимание, что вы должны сделать это на месте, не создавая копию массива.
```
Пример 1:

Ввод: nums = [0,1,0,3,12]
Вывод: [1,3,12,0,0]
Пример 2:

Ввод: nums = [0]
Вывод: [0]
```
## Идея
Два указателя, идущие сначала массива. Один указывает на место куда перемещаем, другой на элемент, который перемещаем.
## Нюансы
-  указатели назвать соответствующее смыслу, что перемещаем и куда перемещаем (target, this)
- Крутить цикл пока указатели не встанут на нужные значения
- Указатель  this может перегонять target, в этом случае target надо сдвигать до this
## Решение
```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        target = 0  # Куда перемещаем (ближе к концу на ненулевой элемент)
        this = 0  # Что перемещаем (только нули)

        while target < len(nums):

            if nums[target] == 0:
                # Сдвигаем указатель пока не найдем ненуль, на место которого будет перемещен нуль.
                target += 1
                continue

            if nums[this] != 0:
                # Сдвигаем указатель пока не найдем нуль, чтобы его переместить ближе к концу.
                this += 1
                # target не должен быть меньше this
                target = max(this, target)
                continue
            
            if nums[this] == 0 and nums[target] != 0:
                nums[this], nums[target] = nums[target], nums[this]
                this += 1
                target += 1
            
        return nums
        
```
Оценка по памяти `O(1)`

Оценка по времени `O(n)`