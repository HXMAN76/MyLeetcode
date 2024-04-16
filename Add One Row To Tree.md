# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
*We could definitely solve this a number of ways, but I'm always partial to* **recursion** *when possible, especially when you can simply recurse the main function rather than having to define a separate recursive helper function. 
The recursive route is a depth-first search `(DFS) solution.`*
# Approach
<!-- Describe your approach to solving the problem. -->
*We can use the `depth` variable as a countdown of sorts, decrementing it as we traverse downward through the tree until we get to our destination row. Since we're going to need to attach the new nodes at `depth` to their parents, we should actually perform our operations when `d = 2`, rather than `d = 1`, so that we have access to the `parent node`.*

*This also allows us to deal with the sticky edge case of when the original value of d is 1.*

*The function will return the `node` each recursion, but since we're not doing anything with the return value when the the function is called internally, it will only really be meaningful on the original function call.*

*This works because we're passing node references through the recursion, so the tree object is being modified regardless of return values.*

---


# Complexity
- Time complexity: $$O(n)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(n)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
**where `n` is the number of nodes in the binary tree.**

---


# My Submission
![Screenshot 2024-04-16 101238.png](https://assets.leetcode.com/users/images/6ec16e39-5d95-4732-955b-bf5d03be9705_1713243273.2400396.png)


# Let's Code it down
```
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def addOneRow(self, root, val, depth):
        """
        :type root: TreeNode
        :type val: int
        :type depth: int
        :rtype: TreeNode
        """
        if depth == 1:
            return TreeNode(val,root,None)
        elif depth == 2:
            root.left = TreeNode(val,root.left,None)
            root.right = TreeNode(val,None,root.right)
        else:
            if root.left : self.addOneRow(root.left,val,depth - 1)
            if root.right : self.addOneRow(root.right,val,depth - 1)
        return root   
```
> Have a nice day , upvote if you understood the solution.
