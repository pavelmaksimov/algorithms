# [Binary Tree Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/description/)

## Задача
Дан корень двоичного дерева, верните значения всех его узлов.
```
Input: root = [1,null,2,3]
Output: [1,2,3]

Input: root = []
Output: []

Input: root = [1]
Output: [1]
```

## Идея
Нужно использовать стек. При обходе узлов, добавлять в стек новые узлы для обхода.

## Решение 
1. Создать стек и положить в него первый узел
2. Далее запустить цикл, пока стек не пуст
3. Извлечь узел
4. Проверить, что он не None
5. Если есть добавить значение в результирующий массив
6. В стек слева добавить узлы слева
7. Потом добавить в стек узлы справа
8. В конце вернуть результат

```python
from collections import deque

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        stack = deque([root])
        result = []

        while stack:
            node = stack.pop()
            if node:
                result.append(node.val)
                stack.append(node.right)
                stack.append(node.left)
        
        return result
```

Оценка по памяти `O(h)`, `h` это глубина дерева, кол-во вершин. В худшем случае, когда дерево как бамбук, без ветвей, ответвляется только по одной ветке, тогда это будет `O(n)`.
  
Оценка по времени `O(n)` один обход в цикле, зависит от кол-ва узлов.