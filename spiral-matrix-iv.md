
# Intuition
The goal is to fill a 2D matrix in a spiral order using the values from a linked list. The key is to manage the boundaries of the matrix while iterating through the linked list. As we fill the matrix, we need to adjust our boundaries to ensure we don't overwrite any values or go out of bounds.

# Approach
1. **Initialize the Matrix**: Create a 2D array (matrix) of size `rows x columns` and fill it with a default value (e.g., -1) to indicate unfilled positions.
2. **Define Boundaries**: Use four variables to keep track of the current boundaries: `topRow`, `bottomRow`, `leftColumn`, and `rightColumn`.
3. **Iterate Through the Linked List**: While there are still nodes in the linked list (`head != null`), fill the matrix in the following order:
   - **Left to Right**: Fill the topmost row from the left boundary to the right boundary, then increment the `topRow`.
   - **Top to Bottom**: Fill the rightmost column from the top boundary to the bottom boundary, then decrement the `rightColumn`.
   - **Right to Left**: Fill the bottommost row from the right boundary to the left boundary, then decrement the `bottomRow`.
   - **Bottom to Top**: Fill the leftmost column from the bottom boundary to the top boundary, then increment the `leftColumn`.
4. **Repeat**: Continue this process until all nodes in the linked list have been placed into the matrix.

# Complexity
- Time complexity: $$O(n)$$, where `n` is the number of nodes in the linked list. Each node is processed exactly once.
- Space complexity: $$O(m)$$, where `m` is the size of the matrix, which is `rows x columns`. This space is used to store the matrix itself.
---
<a href = https://leetcode.com/problems/spiral-matrix-iv/submissions/1383865613/>![image.png](https://assets.leetcode.com/users/images/b6217b2c-15ae-47af-8365-1c98194fd8c9_1725856386.6318269.png)</a>

# Code
```java []
class Solution {
    public int[][] spiralMatrix(int rows, int columns, ListNode head) {
        int[][] matrix = new int[rows][];
        for (int i = 0; i < rows; i++) {
            matrix[i] = new int [columns];
            Arrays.fill(matrix[i], -1);
        }

        int topRow = 0, bottomRow = rows - 1, leftColumn = 0, rightColumn = columns - 1;
        while (head != null) {
        
            for (int col = leftColumn; col <= rightColumn && head != null; col++) {
                matrix[topRow][col] = head.val;
                head = head.next;
            }
            topRow++;

        
            for (int row = topRow; row <= bottomRow && head != null; row++) {
                matrix[row][rightColumn] = head.val;
                head = head.next;
            }
            rightColumn--;

 
            for (int col = rightColumn; col >= leftColumn && head != null; col--) {
                matrix[bottomRow][col] = head.val;
                head = head.next;
            }
            bottomRow--;

       
            for (int row = bottomRow; row >= topRow && head != null; row--) {
                matrix[row][leftColumn] = head.val;
                head = head.next;
            }
            leftColumn++;
        }

        return matrix;
    }
}
```
