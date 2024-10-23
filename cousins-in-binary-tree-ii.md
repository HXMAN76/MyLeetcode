# Intuition  
The problem requires us to replace the value of each node in a binary tree with the sum of all values at the same level, excluding the value of the node itself. To achieve this, we need to traverse the tree level by level (breadth-first), calculate the sum of values at each level, and update each node's value accordingly.  

# Approach  
1. **Breadth-First Search (BFS)**: We will use a queue to perform a level-order traversal of the tree. This allows us to process each level of the tree one at a time.  
2. **Level Sum Calculation**: For each level, we will maintain a sum of all node values. As we traverse each node, we will compute the new value for each node as the previous level's sum minus the node's original value.  
3. **Sibling Sum Calculation**: While processing each node, we will also compute the sum of its children (siblings) and update their values accordingly.  
4. **Update Previous Level Sum**: After processing all nodes at the current level, we will update the previous level sum to be used for the next level.  

This approach ensures that we correctly update each node's value based on the specified rules while maintaining the structure of the tree.  

# Complexity  
- Time complexity: $$O(n)$$, where $$n$$ is the number of nodes in the tree. Each node is processed exactly once.  
- Space complexity: $$O(n)$$ in the worst case due to the queue used for BFS, which can hold up to all nodes at the last level of the tree.
---
<a href = https://leetcode.com/problems/cousins-in-binary-tree-ii/submissions/1431346317/>![image.png](https://assets.leetcode.com/users/images/d3c5f1a3-c526-416c-a7c2-4754420799da_1729680949.632743.png)</a>

# Code
```java []
class Solution {

    public TreeNode replaceValueInTree(TreeNode root) {
        if (root == null) {
            return root;
        }

        Queue<TreeNode> nodeQueue = new LinkedList<>();
        nodeQueue.offer(root);
        int previousLevelSum = root.val;

        while (!nodeQueue.isEmpty()) {
            int levelSize = nodeQueue.size();
            int currentLevelSum = 0;

            for (int i = 0; i < levelSize; i++) {
                TreeNode currentNode = nodeQueue.poll();
                // Update node value to cousin sum
                currentNode.val = previousLevelSum - currentNode.val;

                // Calculate sibling sum
                int siblingSum =
                    (currentNode.left != null ? currentNode.left.val : 0) +
                    (currentNode.right != null ? currentNode.right.val : 0);

                if (currentNode.left != null) {
                    currentLevelSum += currentNode.left.val; // Accumulate current level sum
                    currentNode.left.val = siblingSum; // Update left child's value
                    nodeQueue.offer(currentNode.left); // Add to queue for next level
                }
                if (currentNode.right != null) {
                    currentLevelSum += currentNode.right.val; // Accumulate current level sum
                    currentNode.right.val = siblingSum; // Update right child's value
                    nodeQueue.offer(currentNode.right); // Add to queue for next level
                }
            }

            previousLevelSum = currentLevelSum; // Update previous level sum for next iteration
        }
        return root;
    }
}
```
