# Intuition  
The problem involves removing stones from a grid based on their row and column positions. The key insight is that if two stones share the same row or column, they can be considered connected, and removing one will allow the removal of the others in that connected component. The goal is to maximize the number of stones removed, which translates to finding the number of connected components in the graph formed by the stones.  

# Approach  
To solve this problem, we can use the Union-Find (Disjoint Set Union) data structure to efficiently group stones that are in the same row or column. The approach involves the following steps:  

1. **Initialize Union-Find Structures**: Create two arrays, `parent` and `rank`, to manage the connected components of stones. The `parent` array keeps track of the leader of each component, while the `rank` array helps in optimizing the union operation.  

2. **Map Rows and Columns**: Use dictionaries to keep track of the last seen stone in each row and column. This allows us to quickly find and union stones that are in the same row or column.  

3. **Union Operations**: For each stone, check if its row or column has been seen before. If it has, perform a union operation between the current stone and the previously seen stone in that row or column. Count the number of successful unions, which corresponds to the number of stones that can be removed.  

4. **Return the Result**: The result is the total number of stones that can be removed, which is equal to the number of successful union operations.  

# Complexity  
- Time complexity: $$O(n)$$, where $$n$$ is the number of stones. Each union and find operation is nearly constant time due to path compression and union by rank.  

- Space complexity: $$O(n)$$, for storing the `parent` and `rank` arrays as well as the dictionaries for rows and columns.
---
<a href = "https://leetcode.com/problems/most-stones-removed-with-same-row-or-column/submissions/1371878348/">![image.png](https://assets.leetcode.com/users/images/89849cdd-ec9a-4e80-844f-e8be8641008d_1724910973.0803835.png)</a>
# Code
```python3 []
class Solution:
    def removeStones(self, stones: List[List[int]]) -> int:
        n = len(stones)
        rank = [1] * n
        parent = [i for i in range(n)]
        
        def union(i, j):
            i, j = find(i), find(j)
            if i == j:
                return 0
            if rank[i] < rank[j]:
                i, j = j, i
            rank[i] += rank[j]
            parent[j] = parent[i]
            return 1
        
        def find(i):
            while i != parent[i]:
                parent[i] = i = parent[parent[i]]
            return i
        
        rows, cols = {}, {}
        removed = 0
        for i, (row, col) in enumerate(stones):
            if row in rows:
                removed += union(i, rows[row])
            else:
                rows[row] = i
            if col in cols:
                removed += union(i, cols[col])
            else:
                cols[col] = i
        
        return removed
```
---
# Intuition  
The problem requires determining the maximum number of stones that can be removed from a grid based on their row and column positions. The primary idea is to identify groups of stones that are connected by sharing rows or columns. We can think of these groups as connected components in a graph, where stones are nodes, and an edge exists between two stones if they share a row or a column.  

# Approach  
To solve this problem using a graph traversal technique, we can follow these steps:  

1. **Create an Adjacency List**: We build an adjacency list representing the connections between stones based on their row or column positions. If two stones share the same row or column, we add each stone to the other's adjacency list.  

2. **Depth-First Search (DFS)**: We use DFS to explore the connected components in the graph. We maintain a `visited` list to track which stones have already been checked. Each call to DFS will mark all stones in the same connected component as visited.  

3. **Count Connected Components**: For every unvisited stone, we initiate a DFS, which signifies discovering a new connected component. We count these components.  

4. **Calculate Removable Stones**: The total number of stones that can be removed is equal to the total number of stones minus the number of connected components (since at least one stone in each component must remain).  

# Complexity  
- Time complexity: $$O(n^2)$$, where $$n$$ is the number of stones. This arises from checking each pair of stones to build the adjacency list.  

- Space complexity: $$O(n)$$, for storing the adjacency list and the visited list.
---
<a href = "https://leetcode.com/problems/most-stones-removed-with-same-row-or-column/submissions/1371876347/">![image.png](https://assets.leetcode.com/users/images/d4f04155-4a12-4406-be95-67e33c6f7944_1724911104.3990154.png)</a>

```python3 []
class Solution:
    def removeStones(self, stones: List[List[int]]) -> int:
        n =  len(stones)
        adj_list = [[] for _ in range(n)]
        for i in range(n):
            for j in range(i+1, n):
                if stones[i][0] == stones[j][0] or stones[i][1] == stones[j][1]:
                    adj_list[i].append(j)
                    adj_list[j].append(i)
        
        connections = 0
        visited = [False] * n

        def dfs(stone):
            visited[stone] = True
            for neighbour in adj_list[stone]:
                if not visited[neighbour]:
                    dfs(neighbour)

        for i in range(n):
            if not visited[i]:
                dfs(i)
                connections += 1
                
        return n - connections
```
