```python
class NumMatrix:

    def __init__(self, matrix: List[List[int]]):
        self.matrix = matrix

        # Создание префиксного массива. Число в ячейке, это число ячейки плюс сумма всех сверху
        cols = len(matrix[0])
        rows = len(matrix)
        self.prefix_matrix = [[0 for col in range(cols+1)] for row in range(rows+1)]

        for row in range(1, rows+1):
            for col in range(1, cols+1):
                current_value = matrix[row-1][col-1]
                up_sum = self.prefix_matrix[row-1][col]
                self.prefix_matrix[row][col] = current_value + up_sum

    def sumRegion(self, row1: int, col1: int, row2: int, col2: int) -> int:
        return (
            sum(self.prefix_matrix[row2+1][col1+1:col2+1]) 
            - sum(self.prefix_matrix[row1+1-1][col1+1:col2+1])
            )

в sumRegion, неправильно окно взял
На один столбец меньше
надо [col1+1:col2+2] (+2 а не +1)
```