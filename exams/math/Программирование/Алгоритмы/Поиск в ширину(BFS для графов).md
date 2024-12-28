source: [[Программирование/Алгоритмы/Алгоритмы|Алгоритмы]]
tegs #алгоритмы

**Поиск в ширину (Breadth-First Search, BFS).**

BFS исследует все вершины на одном уровне перед тем, как перейти к следующему уровню.

```cpp
from collections import deque

def bfs(graph, start):
    visited = set()
    queue = deque([start])
    while queue:
        vertex = queue.popleft()
        if vertex not in visited:
            visited.add(vertex)
            print(vertex)
            queue.extend(graph[vertex])

graph = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
}

bfs(graph, 'A')
```

Граф выглядит так - 

        A  
       / \  
      B   C  
     / \   \  
    D   E   F  
         \ /  
          F

Алгоритм BFS начнёт с вершины **A** и пройдёт по графу в таком порядке:

1. Посетит **A**.
2. Перейдёт к вершинам **B** и **C**.
3. Затем посетит **B** и **C**.
4. Перейдёт к вершинам **D**, **E**, и **F**.
5. Затем посетит **D**, **E**, и **F**.

А вот и вывод.