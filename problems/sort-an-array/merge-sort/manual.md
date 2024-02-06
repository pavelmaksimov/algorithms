# [Merge Sort](https://leetcode.com/problems/sort-an-array/post-solution/?submissionId=1167995400)
## Идея
Метод "разделяй и властвуй"
Пополам делим массив, до тех пор, пока не образуются куски меньшие или равные 2 ячейкам.
Парные элементы сравниваются, меньший ставится слева.

Оптимизация:
Чтоб не поймать переполнение стека при рекурсии, можно сортировать другой сортировкой, если элементов меньше 32.

Вместо рекурсии, можно использовать стек.
## Нюансы
- не забыть копировать список с отсортированными элементами перед соединением
## Решение
```python
class Solution:
    def split_and_merge(self, nums: List[int], left, right):
        if right - left == 0:
            pass

        elif right - left == 1:
            if nums[left] > nums[right]:
                nums[left], nums[right] = nums[right], nums[left]

            pass
        else:
            mid = (left + right) // 2
            l, r = self.split_and_merge(nums, left, mid)
            l2, r2 = self.split_and_merge(nums, mid + 1, right)

            nums1 = nums[l:r+1]
            nums2 = nums[l2:r2+1]
            p1, p2 = 0, 0
            i = left

            while i <= right:
                if p1 > len(nums1) - 1:
                    nums[i] = nums2[p2]
                    p2 += 1
                elif p2 > len(nums2) - 1:
                    nums[i] = nums1[p1]
                    p1 += 1
                elif nums1[p1] < nums2[p2]:
                    nums[i] = nums1[p1]
                    p1 += 1
                else:
                    nums[i] = nums2[p2]
                    p2 += 1

                i += 1

        return left, right

    def sortArray(self, nums: List[int]) -> List[int]:
        self.split_and_merge(nums, 0, len(nums) - 1)
        return nums
```

Оценка по времени `O(n log n)`

Дробление занимает `O(log n)`. Соединение `O(n)`.

Оценка по памяти `O(2n)` =  `O(n)`
