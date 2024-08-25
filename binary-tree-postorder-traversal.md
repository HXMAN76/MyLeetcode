# Intuition  
To solve the problem of postorder traversal of a binary tree, my first thought is to visit the left subtree, then the right subtree, and finally the root node. This means that for each node, we need to ensure that both its children are processed before we process the node itself. This naturally leads to a recursive approach where we can build the result list by combining the results from the left and right subtrees with the current node's value.  

# Approach  
The approach involves using a recursive function to traverse the binary tree in postorder. The function will first check if the current node (`root`) is `None`. If it is, we return an empty list. Otherwise, we recursively call the function on the left child and the right child, collecting their results. Finally, we append the current node's value to the result list. The concatenated result from the left subtree, right subtree, and the current node's value will be returned.  

# Complexity  
- Time complexity: $$O(n)$$  
  - Each node in the binary tree is visited exactly once, where `n` is the number of nodes in the tree.  
  
- Space complexity: $$O(n)$$  
  - The space complexity is primarily due to the recursion stack in the worst case (when the tree is skewed), which can go as deep as `n`. Additionally, the space used to store the result list is also `O(n)`.
---
<a href = https://leetcode.com/problems/binary-tree-postorder-traversal/submissions/1367485221/>![image.png](https://assets.leetcode.com/users/images/bd4cd043-988c-4086-86d1-760f4a9aa228_1724562566.4891875.png)</a>
# Code
```python3 []
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        if root is None:
            return []
        result = self.postorderTraversal(root.left)
        result += self.postorderTraversal(root.right)
        result += [root.val]
        return result
```
