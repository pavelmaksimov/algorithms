```python
class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> Optional[ListNode]:
        prev = None
        current = headA

        while current:
            next = current.next
            current.next = prev
            prev = current
            current = next
        
        is_intersect = False
        pointer = headB
        while pointer:
            if pointer == headA:
                is_intersect = True
                break
            
            pointer = pointer.next

        if not is_intersect:
            return 

        current = headA
        while current:
            next = current.next
            current.next = prev
            prev = current
            current = next
        
        pointer_a = headA
        while pointer_a:
            pointer_b = headB

            while pointer_b:
                if pointer_a == pointer_b:
                    return pointer_a

                pointer_b = pointer_b.next

            pointer_a = pointer_a.next
Input
8
[4,1,8,4,5]
[5,6,1,8,4,5]
2
3
Output
Intersected at '4', ERROR: linked structure was modified.
Expected
Intersected at '8'

При повторном развороте первого списка, неправильно поставил указатели 
```