# Approach
> 1. If the root node is null, return 0.
> 2. If root's left node is not null and root left's left node is null and root left's right node is null then value stores the value of the root's left node which is  basically the last node of tree.
> 3. Call the function recursively for root's left and right node and sum them up and return the sum.

---


# Complexity
- Time complexity: $$O(n)$$, Where n is known as number of nodes
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(H)$$, Where H is known as the height of the tree which makes stack in recursive calls
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

---


# My Submission
![Screenshot 2024-04-14 160614.png](https://assets.leetcode.com/users/images/82f211f0-bb2c-4fae-8c57-f0dc1f587e4a_1713091017.8407876.png)

---


# Let's Code it down
```
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def sumOfLeftLeaves(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        value = 0
        if root is None:
            return 0
        if root.left and root.left.left is None and root.left.right is None:
            value = root.left.val
        return value + self.sumOfLeftLeaves(root.right) + self.sumOfLeftLeaves(root.left)
        
```
> Have a nice day and do upvote if you understood the solution
