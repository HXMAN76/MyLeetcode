# Algorithm for Maximum Safeness Factor

## Problem Statement
Given a grid representing a city where each cell can be either empty or occupied by a thief, find the maximum safeness factor such that there exists a path from the top-left corner to the bottom-right corner with a minimum safeness factor.

## Solution Approach

### Step 1: Initialization
1. Initialize a deque `multi_source_queue` to store the coordinates of thieves.
2. Mark thief cells with 0 and empty cells with -1. Push thief coordinates to the queue.

### Step 2: Calculate Safeness Factor
1. Use Breadth-First Search (BFS) to calculate the safeness factor for each cell.
2. For each thief cell in the queue, explore its neighboring cells using BFS and update their safeness factors.

### Step 3: Binary Search for Maximum Safeness Factor
1. Initialize `start` and `end` for binary search as 0 and maximum safeness factor found in the grid.
2. Perform binary search to find the maximum safeness factor such that a valid path exists from the top-left corner to the bottom-right corner.
3. Update `res` with the valid maximum safeness factor.

### Step 4: Check Valid Path
1. Define a function `isValidSafeness` to check if a valid path exists from the top-left corner to the bottom-right corner with the given minimum safeness factor.
2. Use BFS to traverse the grid and check if a valid path exists with the given minimum safeness factor.
3. Return `True` if a valid path exists; otherwise, return `False`.

### Step 5: Utility Functions
1. `isValidCell(grid, i, j)`: Check if a given cell lies within the grid.
2. `isValidSafeness(grid, min_safeness)`: Check if a path exists with the given minimum safeness value.

### Step 6: Output
1. Return the maximum safeness factor (`res`) found.

## Time Complexity
- Let `n` be the size of the grid.
- The time complexity of BFS is $$O(n^2)$$.
- Binary search has a time complexity of $$O(log(m))$$.
- Overall time complexity is $$O(n^2 * log(m))$$.
- Where `m` is `maxsafeness` 

## Space Complexity
- The space complexity is O(n^2) for the grid and additional queues.

# My Submission
<a href = https://leetcode.com/problems/find-the-safest-path-in-a-grid/submissions/1258352097/>![image.png](https://assets.leetcode.com/users/images/96104e50-8c89-45cc-a6b9-90722391a73b_1715743864.2603345.png)</a>

# My Code
```
class Solution:

    # Directions for moving to neighboring cells: right, left, down, up
    dir = [(0, 1), (0, -1), (1, 0), (-1, 0)]

    def maximumSafenessFactor(self, grid: List[List[int]]) -> int:
        n = len(grid)

        multi_source_queue = deque()
        # Mark thieves as 0 and empty cells as -1, and push thieves to the queue
        for i in range(n):
            for j in range(n):
                if grid[i][j] == 1:
                    # Push thief coordinates to the queue
                    multi_source_queue.append((i, j))
                    # Mark thief cell with 0
                    grid[i][j] = 0
                else:
                    # Mark empty cell with -1
                    grid[i][j] = -1

        # Calculate safeness factor for each cell using BFS
        while multi_source_queue:
            size = len(multi_source_queue)
            while size > 0:
                curr = multi_source_queue.popleft()
                # Check neighboring cells
                for d in self.dir:
                    di, dj = curr[0] + d[0], curr[1] + d[1]
                    val = grid[curr[0]][curr[1]]
                    # Check if the cell is valid and unvisited
                    if self.isValidCell(grid, di, dj) and grid[di][dj] == -1:
                        # Update safeness factor and push to the queue
                        grid[di][dj] = val + 1
                        multi_source_queue.append((di, dj))
                size -= 1

        # Binary search for maximum safeness factor
        start, end, res = 0, 0, -1
        for i in range(n):
            for j in range(n):
                # Set end as the maximum safeness factor possible
                end = max(end, grid[i][j])

        while start <= end:
            mid = start + (end - start) // 2
            if self.isValidSafeness(grid, mid):
                # Store valid safeness and search for larger ones
                res = mid
                start = mid + 1
            else:
                end = mid - 1

        return res
    
    # Check if a given cell lies within the grid
    def isValidCell(self, grid, i, j) -> bool:
        n = len(grid)
        return 0 <= i < n and 0 <= j < n

    # Check if a path exists with given minimum safeness value
    def isValidSafeness(self, grid, min_safeness) -> bool:
        n = len(grid)

        # Check if the source and destination cells satisfy minimum safeness
        if grid[0][0] < min_safeness or grid[n - 1][n - 1] < min_safeness:
            return False

        traversal_queue = deque([(0, 0)])
        visited = [[False] * n for _ in range(n)]
        visited[0][0] = True

        # Breadth-first search to find a valid path
        while traversal_queue:
            curr = traversal_queue.popleft()
            if curr[0] == n - 1 and curr[1] == n - 1:
                return True  # Valid path found

            # Check neighboring cells
            for d in self.dir:
                di, dj = curr[0] + d[0], curr[1] + d[1]
                # Check if the neighboring cell is valid and unvisited
                if self.isValidCell(grid, di, dj) and not visited[di][dj] and grid[di][dj] >= min_safeness:
                    visited[di][dj] = True
                    traversal_queue.append((di, dj))

        return False  # No valid path found
```
# Best code
```
class Solution:
    def maximumSafenessFactor(self, grid: List[List[int]]) -> int:
        row, col = len(grid), len(grid[0])
        if grid[0][0] == 1 or grid[row-1][col-1] == 1:
            return 0
        safeness = [[-1]*col for _ in range(row)]
        q = deque([])

        for r in range(row):
            for c in range(col):
                if grid[r][c] == 1:
                    safeness[r][c] = 0
                    q.append((0, r, c))
        
        direction = [(-1,0),(1,0),(0,-1),(0,1)]
        while q:
            dis, r, c = q.popleft()
            for dr, dc in direction:
                nr, nc = r + dr, c + dc
                if 0 <= nr < row and 0 <= nc < col and safeness[nr][nc] == -1:
                    safeness[nr][nc] = dis + 1
                    q.append((dis + 1, nr, nc))
        
        heap = [(-safeness[row-1][col-1], row - 1, col - 1)]
        seen = set([(row-1,col-1)])

        while heap:
            dis, r, c = heappop(heap)
            if (r, c) == (0, 0):
                return -dis
                
            for dr, dc in direction:
                nr, nc = r + dr, c + dc
                if 0 <= nr < row and 0 <= nc < col and (nr, nc) not in seen:
                    safe = max(dis, -safeness[nr][nc])
                    heappush(heap, (safe, nr, nc))
                    seen.add((nr, nc))
        
        return -1
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
