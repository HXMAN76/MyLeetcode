
# Algorithm
**Base Case**: If the current node (`root`) is `NULL`, we simply return `NULL`.  
2. **Swap Children**: Store the left child in a temporary variable, then assign the right child to the left, and the temporary variable (original left child) to the right.  
3. **Recursive Calls**: Recursively call the function on the new left and right children (which were previously the right and left children, respectively).  
4. **Return the Root**: Finally, return the modified root node.  

This approach ensures that we visit every node in the tree exactly once, performing the swap operation at each node.  

# Complexity
- Time complexity: $$O(n)$$, where $$n$$ is the number of nodes in the tree. We visit each node once.  
- Space complexity: $$O(h)$$, where $$h$$ is the height of the tree. This accounts for the space used by the recursion stack. In the worst case (a skewed tree), this could be $$O(n)$$, and in the best case (a balanced tree), it would be $$O(\log n)$$.

<a href= https://leetcode.com/problems/invert-binary-tree/submissions/1432151614/>![image.png](https://assets.leetcode.com/users/images/66f3081c-2be7-4923-bd71-01524943f9f9_1729749614.4900622.png)</a>

# Code
```c []
struct TreeNode* invertTree(struct TreeNode* root) {
    if (root == NULL) {
        return NULL;
    }
    struct TreeNode* L = root->left;
    struct TreeNode* R = root->right;
    root->left = R;
    root->right = L;
    invertTree(root->left);
    invertTree(root->right);
    return root;
}
```
``` java []
class Solution {
    public TreeNode invertTree(TreeNode root) {
        if (root == null) {
            return null;
        }
        TreeNode L = root.left;
        TreeNode R = root.right;
        root.left = R;
        root.right = L;
        invertTree(root.left);
        invertTree(root.right);
        return root;
    }
}
```
