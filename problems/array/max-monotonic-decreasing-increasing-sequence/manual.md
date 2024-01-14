## Задача
Дан массив элементов с числами. Найти самую длинную монотонно убывающую или растущую последовательность. Вернуть индексы среза.
```
Дано = [1, 0, 3, 4, 5, 5]
Результат = [1:6]
Монотонно растущая последовательность здесь [0, 3, 4, 5, 5]
```
## Идея
Сравнение текущего элемента с предыдущим. 
## Нюансы
- Если нужно вернуть индексы срез, то к индексу справа надо добавить единицу.
## Решение
```python
def find(nums):  
    prev = nums[0]  
  
    best_up = (0, 1)  
    l_up = 0  
  
    best_down = (0, 1)  
    l_down = 0  
  
    for i in range(1, len(nums)):  
        current = nums[i]  
  
        # Check up.  
        if current >= prev:  
            best_up = (l_up, i + 1)  
        else:  
            l_up = i  
  
        # Check down.  
        if current <= prev:  
            best_down = (l_down, i + 1)  
        else:  
            l_down = i  
  
        prev = current  
  
    if best_up[1] - best_up[0] > best_down[1] - best_down[0]:  
        return best_up  
    else:  
        return best_down
```
Оценка по памяти `O(1)`

Оценка по времени `O(n)`
