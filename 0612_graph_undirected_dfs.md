# 0612
## Theories
```py
# Graph represented using an adjacency list
graph = {
    'A': ['B', 'C'],
    'B': ['D', 'E'],
    'C': ['F'],
    'D': [],
    'E': ['F'],
    'F': []
}
```
### Traverse all nodes
```py
def dfs(graph, start):
    stack = [start]
    visited = set()

    while stack:
        node = stack.pop()
        if node not in visited:
            visited.add(node)
            print(node)
            for neighbor in graphp[node]:
            stack.append(neighbor)
```
```py
def bfs(graph, start):
    queue = collections.deque([start])
    visited = set([start])

    while queue:
        node = queue.popleft()
        print(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
```

### Traverse all edges
```py
for node, neighbors in graph.items():
    for neighbor in neighbors:
        print(node, '->', neighbor)
```

## Problems
### 133. Clone Graph
```py
"""
# Definition for a Node.
class Node:
    def __init__(self, val = 0, neighbors = None):
        self.val = val
        self.neighbors = neighbors if neighbors is not None else []
"""

class Solution:
    def __init__(self):
        self.visited = {}

    def cloneGraph(self, node: 'Node') -> 'Node':
        if not node:
            return None
        
        if node in self.visited:
            return self.visited[node]

        clone_node = Node(node.val, [])
        self.visited[node] = clone_node

        if node.neighbors:
            clone_node.neighbors = [self.cloneGraph(neighbor) for neighbor in node.neighbors]
        
        return clone_node
        
        # time: O(V + E)
        # space: O(V + E)
        # V: the number of vertices (nodes)
        # E: the number of edges
```

