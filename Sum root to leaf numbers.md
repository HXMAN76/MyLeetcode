# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
> *Create a Recursive call To capture all the numbers in tree , we can multiply them by 10 and add value of the next node.
But we need to store the value to add them up so we make another function which as a variable to store the value then we can sum them up*
# Approach
<!-- Describe your approach to solving the problem. -->
1. Create a new function with 1 variable as an arguement
2. If root is None return 0
3. Append the `value` that is multiply the current value by 10 and add the current value in node.
4. If the node is the last node return the `value`
5. Now recursively call the function for left and right subtree.

# Complexity
- Time complexity: $$O(n)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(n)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def SumNumbers(self,root,val):
        #if root is none return 0
        if root is None:
            return 0
        #else append the value into a variable val 
        val = (val * 10 + root.val)
        
        #if the recursion reached the last node return the val
        if root.left is None and root.right is None:
            return val
        #recursively call the function for all the subtree's nodes
        return (self.SumNumbers(root.left, val) + self.SumNumbers(root.right, val))

    def sumNumbers(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        #calling the recursive function 
        return self.SumNumbers(root,0)
         
```
> Have a great day and please do upvote.

