## Algorithm for evaluating a binary tree

### Function: evaluateTree(root)

1. **Inputs:** 
    - `root`: The root node of a binary tree.
    
2. **Outputs:** 
    - `True` if the binary tree satisfies the specified condition, `False` otherwise.
    
3. **Procedure:**
    - If `root` has no left or right children (i.e., it is a leaf node):
        - Return `True` if `root.val` is equal to 1, indicating the tree satisfies the condition.
    - If `root.val` is equal to 2:
        - Recursively evaluate the left and right subtrees.
        - Return `True` if either the left or right subtree evaluates to `True`.
    - If `root.val` is not equal to 2:
        - Recursively evaluate the left and right subtrees.
        - Return `True` if both the left and right subtrees evaluate to `True`, indicating that the tree satisfies the condition.
        

---

### Example Tree:

Consider the following binary tree:
```
      2
    /   \
   1     2
  / \   / \
 1   0 1   1
```

### Execution:

1. We start evaluating the tree from the root node, which has a value of 2.
2. Since the root node's value is 2, we recursively evaluate its left and right subtrees.
3. For the left subtree:
    - The left child has a value of 1, and it has no children. So, it satisfies the condition.
    - The right child has a value of 0, and it has no children. So, it does not satisfy the condition.
4. For the right subtree:
    - Both the left and right children have values of 1, and they have no children. So, they satisfy the condition.
5. Since the root node's value is 2, and at least one of its subtrees (the right subtree) satisfies the condition, the entire tree satisfies the condition.
6. Therefore, the function returns `True`.
---
## Time Complexity Analysis

The time complexity of the `evaluateTree` function is $$O(n)$$, where $$n$$ is the number of nodes in the binary tree.

- In the worst case, the function needs to traverse all nodes of the binary tree once.
- At each node, there are constant-time operations involved (comparisons and recursive calls).

Therefore, the time complexity is linear with respect to the number of nodes in the binary tree.

## Space Complexity Analysis

The space complexity of the `evaluateTree` function depends on the depth of the recursion stack and additional memory usage for storing function parameters and local variables.

- In the worst case, if the binary tree is unbalanced (resembling a linked list), the depth of the recursion stack could be $$O(n)$$.
- In the best case, if the binary tree is balanced, the depth of the recursion stack is $$O(log n)$$, where n is the number of nodes in the binary tree.
- Additionally, there is a negligible amount of space used for storing function parameters and local variables.

Therefore, the space complexity is $$O(n)$$ in the worst case and $$O(log\ n)$$ in the best case.

---
# My Submission
<a href = https://leetcode.com/problems/evaluate-boolean-binary-tree/submissions/1259264439/>![image.png](https://assets.leetcode.com/users/images/2bd5ba43-ff92-4fd4-8b13-e4c62fbc44a3_1715832730.954279.png)</a>

# Code
```
class Solution:
    def evaluateTree(self, root: Optional[TreeNode]) -> bool:
        
        if not root.left and not root.right:
            return root.val == 1
        
        if root.val == 2:
            return self.evaluateTree(root.left) or self.evaluateTree(root.right)
        else:
            return self.evaluateTree(root.left) and self.evaluateTree(root.right)


```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
