# Magic Square Detection in a 2D Grid  

The following Python code defines a solution to count the number of **3x3 magic squares** within a larger 2D grid. A magic square of size 3x3 is a grid where the numbers from 1 to 9 are arranged so that the sums of the numbers in each row, each column, and the two main diagonals all equal 15.  

## Code Overview  

### Class Definition  

The code outlines a class named `Solution` which contains a method for counting magic squares.  

### Method: `numMagicSquaresInside`  

This method takes a 2D list `grid` as input, which represents the larger grid where we search for 3x3 magic squares.  

### Helper Function: `isMagic(i, j)`  

The function `isMagic(i, j)` checks if the 3x3 square centered at the grid position `(i, j)` is a magic square.  

#### Initialization  

- `once`: A boolean array to track the uniqueness of numbers from 1 to 9 (index 0 is unused).  
- `rowSum`: An array to calculate the sum of the three rows in the 3x3 square.  
- `colSum`: An array to calculate the sum of the three columns in the 3x3 square.  

#### Loop Through the Subgrid  

- Nested loops iterate over the cells of the 3x3 area around `(i, j)` (from `(i-1, j-1)` to `(i+1, j+1)`).  
- For each cell:  
  - Check if the number is between 1 and 9. If not, return `False`.  
  - Update the sums of the rows and columns.  
  - Check for duplicates using the `once` array. If a number appears more than once, return `False`.  

#### Final Checks  

After collecting the sums:  
- Ensure all numbers from 1 to 9 are present (verified via the `once` array).  
- Check that each row and column's sum equals 15.  
- Verify the sums of the diagonals equal 10 (specific corner checks).  

### Main Logic  

- Retrieve the dimensions of `grid` and check if it has at least 3 rows and 3 columns. If not, return 0 (no magic squares possible).  
- Initialize a counter `cnt` to track the number of magic squares found.  
- Loop through each potential center position `(i, j)` of a 3x3 square (from `1` to `r-2` for rows and `1` to `c-2` for columns).  
- For each center:  
  - Check if the middle cell is 5 (a requirement for magic squares).  
  - Check if the 3x3 square is magic by calling the `isMagic(i, j)`. If both conditions are met, increment `cnt`.  

### Return Value  

Finally, the method returns the count of magic squares found in the grid.  

## Summary  

This code efficiently checks each 3x3 region in the grid to determine if it forms a magic square, specifically counting those that meet the specified conditions.

# Complexity
- Time complexity: $$O(r \ * \ c)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(1)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution:
    def numMagicSquaresInside(self, grid: List[List[int]]) -> int:
        def isMagic(i, j):
            once=[False]*10
            rowSum=[0]*3
            colSum= [0]*3

            for a in range(i-1, i+2):
                for b in range(j-1, j+2):
                    x= grid[a][b]
                    if x < 1 or x > 9: return False
                    rowSum[a-i+1] += x
                    colSum[b-j+1] += x
                    if once[x]: 
                        return False  # it's not unique
                    once[x]=True

            for b in once[1:]: 
                if not b: return False

            for sum in rowSum:
                if sum!=15: return False
            for sum in colSum:
                if sum!=15: return False
            
            return grid[i-1][j-1]+grid[i+1][j+1]==10 and grid[i+1][j-1]+grid[i-1][j+1]==10
        
        r, c = len(grid), len(grid[0])
        if r < 3 or c < 3: 
            return 0

        cnt=0
        for i in range(1, r-1):
            for j in range(1, c-1):
                if grid[i][j] == 5 and isMagic(i, j): 
                    cnt+=1
        return cnt        
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)

