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
