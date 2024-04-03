# Question
Given an m x n grid of characters board and a string word, return true if word exists in the grid.

The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We can go over each element in the grid by using a simple traversal and for each cell, we can call a DFS function which will check if starting from that r,c cell, if the searchword is found. If it’s found, then we can return true and else continue to search for the next cell pair. If no match is found and we have reached the end of our traversal of the 2D matrix, then return False


# Approach
<!-- Describe your approach to solving the problem. -->
Such a DFS function will accept 3 parameters:

- Current row id
- Current column id
- Id of word character we want to find

The function will first check for the valid case which is when the word is found. We check if we reach the bottom case of the recursion, where the word to be matched is empty, i.e. we have already found the match for each prefix of the word. We can check this by checking if the ith character is equal to the length of the word to be matched. In such a case, return True

Then it will return False for any invalid cases, some of these invalid cases are:

- The values of r and c are out of bounds
- The i character we are looking for has not been found on the board
- This r,c (representing a cell) was already visited


# Complexity
- Time complexity: *O(N⋅3^L)*
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: *O(L)*
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
> where N is the number of cells in the board and L is the length of the word to be matched.

---

# Let’s code 👨🏻‍💻
```
class Solution(object):
    def exist(self, board, word):
        """
        :type board: List[List[str]]
        :type word: str
        :rtype: bool
        """
        R = len(board)
        C = len(board[0])

        visited= set()
        def findExist(r,c,i):
            """
            Base case: if last char then return true
            """
            if i == len(word):
                return True
            """
            if any exceptions like out of bound or i-th character mismatch or (r,c) is already visited
            """
            if r < 0 or r >= R or c < 0 or c >= C or word[i] != board[r][c] or (r,c) in visited:
                return False

            visited.add((r,c)) 

            temp = findExist(r + 1, c, i + 1) or findExist(r, c + 1, i + 1) or findExist(r - 1, c, i + 1) or findExist(r, c - 1, i + 1)

            visited.remove((r,c))

            return temp
    
        for r in range(R):
            for c in range(C):
                if findExist(r,c,0):
                    return True

        return False
    

```
