# Spiral Matrix III Solution Explanation  

The provided code defines a class `Solution` with a method `spiralMatrixIII`, which generates the coordinates of the elements in a matrix by moving in a spiral pattern. Here is a detailed breakdown of the code:  

## Code Breakdown  

1. **Class Definition**:  
    ```python  
    class Solution(object):  
    ```  
   - Defines a class named `Solution` that contains the method for generating coordinates.  

2. **Method Definition**:  
    ```python  
    def spiralMatrixIII(self, rows, cols, rStart, cStart):  
    ```  
   - Takes four parameters:  
     - `rows`: the number of rows in the matrix.  
     - `cols`: the number of columns in the matrix.  
     - `rStart`: the starting row index.  
     - `cStart`: the starting column index.  

3. **Initialization**:  
    ```python  
    i,j = rStart, cStart  
    diri, dirj = 0, 1  # directions to move  
    twice = 2  
    res = []  
    moves = 1  
    next_moves = 2  
    ```  
   - Initializes the current position to the starting coordinates.  
   - Sets the initial movement direction to the right (0 for rows, 1 for columns).  
   - `twice` indicates how many turns to make before increasing the number of moves in the next direction.  
   - `res` will store the coordinates of the visited cells.  
   - `moves` tracks how many steps to take in the current direction.  
   - `next_moves` defines the steps to take in the next direction after a full turn.  

4. **While Loop**:  
    ```python  
    while len(res) < (rows * cols):  
    ```  
   - Continues the loop until all cells in the `rows` by `cols` matrix are visited.  
   - Inside the loop:  
     - It checks if the current position `(i, j)` is within matrix bounds. If so, it appends the position to `res`.  
     - The position is updated based on the current direction:  
       ```python  
       i += diri  
       j += dirj  
       ```  
     - Remaining moves in the current direction are decremented by 1.  

5. **Direction Change**:  
    ```python  
    if moves == 0:  
        diri, dirj = dirj, -diri  # 90 deg Clockwise  
        twice -= 1  
        if twice == 0:  
            twice = 2  
            moves = next_moves  
            next_moves += 1  
        else:  
            moves = next_moves - 1  
    ```  
   - If all moves in the current direction are completed:  
     - The direction vectors are updated by rotating clockwise.  
     - It resets or decrements `twice` and manages the number of moves for the next direction.  

6. **Return Statement**:  
    ```python  
    return res  
    ```  
   - Once the loop completes, it returns the list of coordinates stored in `res`.  

## Summary  
The `spiralMatrixIII` method simulates a spiral traversal of a matrix starting from a specific cell `(rStart, cStart)`. It continues moving in a spiral pattern, recording the coordinates of the cells visited until all cells of the matrix are collected in the result list `res`. The movement starts to the right and changes direction (right, down, left, up) while gradually increasing the length of successive segments of the spiral.
# Complexity
- Time complexity: $$O(rows \ *\ cols)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(rows \ *\ cols)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution(object):
    def spiralMatrixIII(self, rows, cols, rStart, cStart):
        i,j = rStart, cStart

        diri, dirj = 0, 1 # directions to move
        twice = 2
        res = []
        moves = 1
        next_moves = 2

        while len(res) < (rows * cols):
            if (-1 < i < rows) and ( -1 < j < cols):
                res.append([i,j])
            
            i += diri
            j += dirj
            moves -= 1
            if moves == 0:
                diri, dirj = dirj, -diri # 90 deg Clockwise
                twice -= 1
                if twice == 0:
                    twice = 2
                    moves = next_moves
                    next_moves += 1
                else:
                    moves = next_moves - 1
        return res
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
