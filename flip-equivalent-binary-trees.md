
# Approach To solve this problem, I will use a recursive approach. The steps are as follows:  
1. If both nodes are `null`, return `true` since they are equivalent.  
2. If one of the nodes is `null`, return `false` since one tree has a node while the other does not.  
3. If the values of the nodes are not equal, return `false`.  
4. Recursively check two scenarios:  
 - Without swapping the children: compare the left child of `root1` with the left child of `root2`, and the right child of `root1` with the right child of `root2`.  
 - With swapping the children: compare the left child of `root1` with the right child of `root2`, and the right child of `root1` with the left child of `root2`.  
5. Return `true` if either of the above scenarios returns `true`.  

This approach ensures that all possible configurations of the trees are checked for equivalence.  

# Complexity
- Time complexity: $$O(n)$$, where $$n$$ is the number of nodes in the trees. Each node is visited once.  
- Space complexity: $$O(h)$$, where $$h$$ is the height of the trees. This accounts for the recursion stack in the worst case (skewed trees).
---
<a href=https://leetcode.com/problems/flip-equivalent-binary-trees/submissions/1432177092/>![image.png](https://assets.leetcode.com/users/images/830c81ce-ff04-402b-a612-cd1d04adb5d9_1729751509.0373738.png)</a>

# Code
```java []
class Solution {
    public boolean flipEquiv(TreeNode root1, TreeNode root2) {
        if (root1 == null) {
            if (root2 == null) {
                return true;
            }
            return false;
        }
        if (root2 == null) {
            return false;
        }
        if (root1.val != root2.val) {
            return false;
        }
        boolean noSwap = flipEquiv(root1.left,root2.left) && flipEquiv(root1.right, root2.right);
        boolean Swap = flipEquiv(root1.left, root2.right) && flipEquiv(root1.right, root2.left);
        return Swap || noSwap;
    }
}
```
