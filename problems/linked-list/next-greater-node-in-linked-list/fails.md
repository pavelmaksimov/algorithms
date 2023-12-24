```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def nextLargerNodes(self, head: Optional[ListNode]) -> List[int]:
        prev = ListNode(float('-inf'))
        pointer = head
        head_pointer = head
        result = []

        while pointer:
            if prev.val < pointer.val:
                prev = pointer
                pointer = pointer.next
            else:
                next_maximum = prev
                
                current = head_pointer
                while current != next_maximum:
                    next = current.next
                    # current.val = next_maximum.val
                    result.append(next_maximum.val)
                    current = next
                
                result.append(0)
                #next_maximum.val = 0
                prev = ListNode(float('-inf'))
                head_pointer = next_maximum.next

        return result
```

По классике, ТЗ не до конца понял, с начала пытался связать ноды, потом понял связи менять не надо, 
менял знаения val в узлах, потом прогнал тест, увидел, что оказывается список интов надо вернуть. 
Переделал, но работает неправильно.

```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def nextLargerNodes(self, head: Optional[ListNode]) -> List[int]:
        # Разворачиваем список.
        length = 0
        prev = None
        current = head
        while current:
            next = current.next
            current.next = prev
            prev = current
            current = next
            length += 1
            
        # Ход с конца в начало теперь.
        # result = [0] # В конце максимум, поэтому 0 ставится
        result = [0] * length # Но лучше сразу создать массив нужной длины
        i = 1
        current_max = prev.val # Это конечный узел
        current = prev.next # Начинаем со второго с конца полчается
        while current:
            if current.val > current_max:
                current_max = current.val
            else:
                result[i] = current.val
                
            next = current.next
            prev = current
            current = next
            i += 1
        
        result.reverse()
        
        return result

Неправильное значение в список добавлял 
result[i] = current.val
Надо максиум
result[i] = current_max
```


```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def nextLargerNodes(self, head: Optional[ListNode]) -> List[int]:
        # Разворачиваем список.
        length = 0
        prev = None
        current = head
        while current:
            next = current.next
            current.next = prev
            prev = current
            current = next
            length += 1
            
        # Ход с конца в начало теперь.
        # result = [0] # В конце максимум, поэтому 0 ставится
        result = [0] * length # Но лучше сразу создать массив нужной длины
        i = 1
        current_max = prev.val # Это конечный узел
        current = prev.next # Начинаем со второго с конца полчается
        while current:
            if current.val > current_max:
                current_max = current.val
            else:
                result[i] = current_max
                
            next = current.next
            prev = current
            current = next
            i += 1
        
        result.reverse()
        
        return result

Input
head = [1,7,5,1,9,2,5,1]
Output [9,9,9,9,0,5,0,0]
Expected [7,9,9,9,0,5,0,0]

Надо обновлять максимум на предыдущее значение, 
если предыдущее значение больше текущего.
```

```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def nextLargerNodes(self, head: Optional[ListNode]) -> List[int]:
        # Разворачиваем список.
        length = 0
        prev = None
        current = head
        while current:
            next = current.next
            current.next = prev
            prev = current
            current = next
            length += 1
            
        # Ход с конца в начало теперь.
        # result = [0] # В конце максимум, поэтому 0 ставится
        result = [0] * length # Но лучше сразу создать массив нужной длины
        i = 1
        current_max = prev.val # Это конечный узел
        current = prev.next # Начинаем со второго с конца полчается
        while current:
            if current.val > current_max:
                current_max = current.val
            elif current.val < prev.val:
                current_max = prev.val
            else:
                result[i] = current_max
                
            next = current.next
            prev = current
            current = next
            i += 1
        
        result.reverse()
        
        return result
    
Ввод head = [3,3]
Вывод [3,0]
Ожидается [0,0]

Когда текущий и максимум равны, надо ставить 0
current.val == current_max
Не обрабатывался такой случай
```

```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def nextLargerNodes(self, head: Optional[ListNode]) -> List[int]:
        # Разворачиваем список.
        length = 0
        prev = None
        current = head
        while current:
            next = current.next
            current.next = prev
            prev = current
            current = next
            length += 1
            
        # Ход с конца в начало теперь.
        # result = [0] # В конце максимум, поэтому 0 ставится
        result = [0] * length # Но лучше сразу создать массив нужной длины
        i = 1
        current_max = prev.val # Это конечный узел
        current = prev.next # Начинаем со второго с конца полчается
        while current:
            if current.val == current_max:
                pass # set 0
            elif current.val > current_max:
                current_max = current.val
                # set 0
            elif current.val < prev.val:
                current_max = prev.val
                result[i] = current_max
            else:
                result[i] = current_max
                # set 0
                
            next = current.next
            prev = current
            current = next
            i += 1
        
        result.reverse()
        
        return result
Ввод = [9,7,6,7,6,9]
Вывод [0,0,7,9,9,0]
Ожидается [0,9,7,9,9,0]
```

Надо было использовать стек.