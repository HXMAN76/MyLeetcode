
# Complexity
- Time complexity: $$O( \ n ^2 \ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:  $$O( \ n ^2 \ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# My Submission
<a href = https://leetcode.com/problems/find-if-path-exists-in-graph/submissions/1238270002/></a>
![Screenshot 2024-04-21 192812.png](https://assets.leetcode.com/users/images/25af0701-b794-43ee-ba98-79f352518cdf_1713708043.8567839.png)

# Code
```
class Solution:
    def validPath(self, n: int, edges: List[List[int]], source: int, destination: int) -> bool:
        graph = collections.defaultdict(list)
        for u, v in edges:
            graph[u].append(v)
            graph[v].append(u)
        
        distances = {node: float('inf') for node in range(n)}
        distances[source] = 0
        priority_queue = [(0, source)]
        
        while priority_queue:
            current_distance, current_node = heapq.heappop(priority_queue)
            if current_node == destination:
                return True
            
            if current_distance > distances[current_node]:
                continue
            
            for neighbor in graph[current_node]:
                distance = current_distance + 1  # Assuming unweighted graph
                if distance < distances[neighbor]:
                    distances[neighbor] = distance
                    heapq.heappush(priority_queue, (distance, neighbor))
        
        return False
```
