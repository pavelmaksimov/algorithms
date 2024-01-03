```python
class Solution:
    def carPooling(self, trips: List[List[int]], capacity: int) -> bool:
        counter = 0
        trips.sort(key=lambda x: x[2])
        start = 0
        end = 0

        while start < len(trips) or end < len(trips):
            if start < len(trips) and trips[start][1] < trips[end][2]:
                start += 1
                capacity -= trips[start][0]
            else:
                end += 1
                capacity += trips[end][0]

            if capacity < 0:
                return False
        
        return True

IndexError

Надо сначала указатели двигать, потом capacity изменять
тут неправильный порядок действий
start += 1
capacity -= trips[start][0]
```