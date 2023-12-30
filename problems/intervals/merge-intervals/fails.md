```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        intervals.sort(key=lambda i: i[1])
        result = [intervals[0]]

        for i in range(1, len(intervals)):
            a, b = intervals[i]
            prev_a, prev_b = result[-1][0], result[-1][1]

            if a <= prev_b:
                result[-1][0] = min(prev_a, a)
                result[-1][1] = b
            else:
                result.append([a, b])

        return result

Input intervals = [[2,3],[4,5],[6,7],[8,9],[1,10]]
Output ?
Expected [[1,10]]

надо сортиовать по a
и брать макисмальный из b и prev_b
```