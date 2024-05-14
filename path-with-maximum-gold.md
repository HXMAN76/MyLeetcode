## Algorithm:

1. **Define Directions:**
   - Define the directions to move (up, right, down, left) relative to the current cell.

2. **Initialize Variables:**
   - Initialize variables to store the number of rows and columns in the grid.

3. **Define BFS Backtrack Function:**
   - Define a function `bfs_backtrack` to perform Breadth-First Search (BFS) with backtracking.
     - Initialize a queue, a set to track visited cells, and a variable to store the maximum gold.
     - Add the starting cell to the queue and mark it as visited.
     - While the queue is not empty:
       - Dequeue a cell and update the maximum gold if needed.
       - Iterate over all four directions:
         - Calculate the next cell's coordinates.
         - If the next cell is within the grid bounds, contains gold, and has not been visited:
           - Add it to the queue with updated gold count and visited set.
     - Return the maximum gold found.

4. **Calculate Total Gold:**
   - Calculate the total gold in the grid.

5. **Iterate Over Grid Cells:**
   - Iterate over each cell in the grid:
     - If the cell contains gold:
       - Find the maximum gold starting from that cell using `bfs_backtrack`.
       - Update the maximum gold found so far.
       - If the maximum gold found is equal to the total gold, return the total gold.

6. **Return Maximum Gold:**
   - Return the maximum gold found.

## Time Complexity:
- The BFS traversal visits each cell at most once, resulting in a time complexity of O(rows * cols).
- Within the BFS traversal, the inner loop iterating over the four directions has constant time complexity.
- Overall time complexity: O(rows * cols).

## Space Complexity:
- The space complexity is dominated by the queue and the visited set.
- The queue can potentially hold all cells in the grid, leading to a space complexity of O(rows * cols).
- The visited set also grows with the number of cells, but it only stores unique visited cells, resulting in a space complexity of O(rows * cols).
- Other auxiliary variables have constant space complexity.
- Overall space complexity: O(rows * cols).

# Complexity
- Time complexity: $$O(rows\ *\ cols )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:$$O(rows\ *\ cols )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
# My Submission
<a href = https://leetcode.com/problems/path-with-maximum-gold/submissions/1257710346/>![image.png](https://assets.leetcode.com/users/images/17516389-9c2a-42a2-8c2f-8db723ac936d_1715681267.7019958.png)</a>
# Code
```
class Solution:
    def getMaximumGold(self, grid: List[List[int]]) -> int:
        DIRECTIONS = [0, 1, 0, -1, 0]
        rows = len(grid)
        cols = len(grid[0])
        
        def bfs_backtrack(row: int, col: int) -> int:
            queue = deque()
            visited = set()
            max_gold = 0
            visited.add((row, col))
            queue.append((row, col, grid[row][col], visited))
            while queue:
                curr_row, curr_col, curr_gold, curr_vis = queue.popleft()
                max_gold = max(max_gold, curr_gold)

                # Search for gold in each of the 4 nieghbor cells
                for direction in range(4):
                    next_row = curr_row + DIRECTIONS[direction]
                    next_col = curr_col + DIRECTIONS[direction + 1]

                    # If the next cell is in the matrix, has gold, 
                    # and has not been visited, add it to the queue
                    if 0 <= next_row < rows and 0 <= next_col < cols and \
                            grid[next_row][next_col] != 0 and \
                            (next_row, next_col) not in curr_vis:
                        curr_vis.add((next_row, next_col))
                        queue.append((next_row, next_col, 
                                      curr_gold + grid[next_row][next_col], 
                                      curr_vis.copy()))
                        curr_vis.remove((next_row, next_col))
            return max_gold

        # Find the total amount of gold in the grid
        total_gold = sum(sum(row) for row in grid)
        
        # Search for the path with the maximum gold starting from each cell
        max_gold = 0
        for row in range(rows):
            for col in range(cols):
                if grid[row][col] != 0:
                    max_gold = max(max_gold, bfs_backtrack(row, col))
                    # If we found a path with the total gold, its the max gold
                    if max_gold == total_gold:
                        return total_gold
        return max_gold
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
