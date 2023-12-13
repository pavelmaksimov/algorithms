```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def getMinimalNode(self, heads):
        min_value = float('inf')
        min_node = None

        for head in heads:
            if head and head.val < min_value:
                min_node = head
                min_value = head.val
        
        return min_node

    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        dummy = ListNode()
        tail = dummy
        
        while 1:
            min_node = self.getMinimalNode(lists)
            if not min_node:
                return dummy.next

            tail.next = min_node
            tail = min_node

        return dummy.next
забыл подвинуть указатель в getMinimalNode на следующиую ноду, после взять минимального
```

```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def getMinimalNode(self, heads):
        min_value = float('inf')
        min_node = None

        for i in range(len(heads)):
            head = heads[i]
            if head and head.val < min_value:
                min_node = head
                min_value = head.val

                heads[i] = head.next
        
        return min_node

    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        dummy = ListNode()
        tail = dummy
        
        while 1:
            min_node = self.getMinimalNode(lists)
            if not min_node:
                return dummy.next

            tail.next = min_node
            tail = min_node
Input
lists =
[[1,4,5],[1,3,4],[2,6]]
Output
[1,1,2,4,6]
Expected
[1,1,2,3,4,4,5,6]

Неправильно начал двигать указатели при взятии минимальной ноды, 
стал двигать у всех, а надо только тогда, когда определил минимальную, у нее подвинуть.
```

```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def getMinimalNode(self, heads):
        min_value = float('inf')
        min_node = None
        min_index = None

        for i in range(len(heads)):
            head = heads[i]
            if head and head.val < min_value:
                min_node = head
                min_value = head.val
                min_index = i

        if min_index:
            heads[min_index] = min_node.next
        
        return min_node

    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        dummy = ListNode()
        tail = dummy
        
        while 1:
            min_node = self.getMinimalNode(lists)
            if not min_node:
                return dummy.next

            tail.next = min_node
            tail = min_node
Time Limit Exceeded

min_index может быть 0 и это нормально, при этом значении не сдвигался указатель
```