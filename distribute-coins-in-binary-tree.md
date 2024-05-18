## Algorithm:

1. **Initialize Moves Counter:**
   - Initialize a counter `self.moves` to keep track of the number of moves required to distribute the coins.

2. **Define DFS Function:**
   - Define a Depth-First Search (DFS) function `dfs` that traverses the tree and calculates the excess coins at each node.
   - If the current node is `None`, return 0 (no excess coins).

3. **Recursive DFS Calls:**
   - Recursively call `dfs` on the left child of the current node to calculate the left excess coins.
   - Recursively call `dfs` on the right child of the current node to calculate the right excess coins.

4. **Update Moves:**
   - Update `self.moves` by adding the absolute values of the left and right excess coins.
   - The absolute values represent the number of moves required to balance the excess coins between the current node and its children.

5. **Calculate and Return Excess Coins:**
   - Calculate the excess coins at the current node as `node.val + left_excess + right_excess - 1`.
   - Return the calculated excess coins to the parent node.

6. **Execute DFS from Root:**
   - Call `dfs` starting from the root of the tree.

7. **Return Total Moves:**
   - Return the value of `self.moves`, which represents the total number of moves required to distribute the coins.

## Time Complexity:
- Each node in the binary tree is visited exactly once, resulting in a time complexity of $$O(n)$$, where n is the number of nodes in the tree.
- The operations performed at each node (calculating excess coins and updating the move counter) take constant time.

## Space Complexity:
- The space complexity is determined by the recursion stack, which depends on the height of the tree.
- In the worst case, the tree is completely unbalanced (e.g., a linked list), resulting in a space complexity of $$O(n)$$.
- In the best case, the tree is perfectly balanced, resulting in a space complexity of $$O(log\ n)$$.
# My Submission
<a href = https://leetcode.com/problems/distribute-coins-in-binary-tree/submissions/1261009323/>![image.png](https://assets.leetcode.com/users/images/63e4e116-9006-4e00-83bb-aadb16204501_1716006767.7522933.png)</a>
# Let's Code it down
```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def distributeCoins(self, root: Optional[TreeNode]) -> int:
        self.moves = 0
        def dfs(node):
            if not node:
                return 0
            left_excess = dfs(node.left)
            right_excess = dfs(node.right)
            self.moves += abs(left_excess) + abs(right_excess)
            return node.val + left_excess + right_excess - 1

        dfs(root)
        return self.moves


```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
