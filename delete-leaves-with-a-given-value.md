# Algorithm:

1. **Base Case:**
   - If the current node (`root`) is `None`, return `None`.

2. **Recursive Calls:**
   - Recursively call `removeLeafNodes` on the left child of the current node.
   - Recursively call `removeLeafNodes` on the right child of the current node.
   - Update the left and right children of the current node with the results of these recursive calls.

3. **Remove Leaf Node:**
   - After the recursive calls, check if the current node is a leaf node (both left and right children are `None`) and its value equals the target.
   - If both conditions are met, return `None` to remove this leaf node.

4. **Return Node:**
   - If the current node is not a target leaf node, return the current node itself.
---
## Time Complexity:
- Each node in the binary tree is visited exactly once, leading to a time complexity of $$O(n)$$, where `n` is the number of nodes in the tree.
- The operations performed at each node (checking the value and updating pointers) take constant time.

## Space Complexity:
- The space complexity is determined by the recursion stack, which depends on the height of the tree.
- In the `worst case`, the tree is completely unbalanced (e.g., a linked list), resulting in a space complexity of $$O(n)$$.
- In the `best case`, the tree is perfectly balanced, resulting in a space complexity of $$O(log\ n)$$.
---
# My Submission
<a href = https://leetcode.com/problems/delete-leaves-with-a-given-value/submissions/1260191185/>![image.png](https://assets.leetcode.com/users/images/8c790a1a-3a3c-45ce-b3d4-ba6f3c29f684_1715920289.1440434.png)</a>

# Code
```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def removeLeafNodes(self, root: Optional[TreeNode], target: int) -> Optional[TreeNode]:
        if not root:
            return None 
        root.left = self.removeLeafNodes(root.left,target)
        root.right = self.removeLeafNodes(root.right,target)
        return None if (root.left is None and root.right is None and root.val == target) else root


```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
