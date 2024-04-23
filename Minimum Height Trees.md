# Complexity
- Time complexity: $$ O( \ n \ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O( \ n \ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# My submission
<a href = https://leetcode.com/problems/minimum-height-trees/submissions/1239673614/>![Screenshot 2024-04-23 122608.png](https://assets.leetcode.com/users/images/9ddf36c4-6e69-4faa-8f93-693975a256f6_1713855423.7176476.png)</a>


# Code
```
class Solution:
    def findMinHeightTrees(self, n: int, edges: List[List[int]]) -> List[int]:
        if n == 1:
            return [0]
        
        # Initialize the adjacency list and degree of each node
        adjacency_list = defaultdict(list)
        degree = [0] * n
        for u, v in edges:
            adjacency_list[u].append(v)
            adjacency_list[v].append(u)
            degree[u] += 1
            degree[v] += 1
        
        # Initialize leaves queue
        leaves = deque([i for i in range(n) if degree[i] == 1])
        
        # Trim leaves until 2 or fewer nodes remain
        remaining_nodes = n
        while remaining_nodes > 2:
            leaves_count = len(leaves)
            remaining_nodes -= leaves_count
            for _ in range(leaves_count):
                leaf = leaves.popleft()
                for neighbor in adjacency_list[leaf]:
                    degree[neighbor] -= 1
                    if degree[neighbor] == 1:
                        leaves.append(neighbor)
        
        return list(leaves)
```
