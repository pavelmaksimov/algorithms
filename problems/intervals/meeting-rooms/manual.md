[Meeting Rooms](https://www.interviewbit.com/problems/meeting-rooms/)

По расписанию встреч, нужно определить кол-во требуемых комнат.

Решение:
1. Добавить счетчик комнат
2. Cтавим два указателя, оба будут указывать на массив, но на разные точки, начала или конца
3. Берем минимальное из них
4. Если из указателя на начальную точку, то прибавляем счетчик комнат
5. Если из указателя на конечную точку, вычитаем комнату
6. Сохраняем максимальное на каждом шаге
```python
class Solution:  
    def solve(self, A: list[int]) -> int:  
        A.sort(key=lambda x: x[1])  
        counter = 0  
        rooms = 0  
  
        start = 0  
        end = 0  
  
        while start < len(A) or end < len(A):  
            if start < len(A) and A[start][0] <= A[end][1]:  
                rooms += 1  
                start += 1  
            else:  
                rooms -= 1  
                end += 1  
  
            counter = max(counter, rooms)  
  
        return counter
```
Оценка по памяти O(n), из-за сортировки, без неё O(1)

Оценка по времени O(n log n) из-за сортировки, без неё O(n)
