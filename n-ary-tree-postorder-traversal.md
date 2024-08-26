# Intuition  
To solve the problem of performing a postorder traversal on an N-ary tree, we need to visit all the children of a node before visiting the node itself. This means we will recursively traverse each child node before appending the current node's value to the result list. The postorder traversal follows the order of visiting all children first and then the parent node.  

# Approach  
1. **Base Case**: If the root is `None`, return an empty list since there are no nodes to traverse.  
2. **Recursive Traversal**: Define a helper function `traverse` that takes the current node and a list to store the results.  
   - For each child of the current node, recursively call the `traverse` function.  
   - After all children have been processed, append the current node's value to the result list.  
3. **Return the Result**: After traversing all nodes, return the result list containing the values in postorder.  

The overall traversal will ensure that we explore all nodes, and the result will be collected in the required postorder format.  

# Complexity  
- Time complexity: $$O(n)$$, where $$n$$ is the number of nodes in the tree, as we visit each node exactly once.  
- Space complexity: $$O(n)$$, due to the recursion stack and the space required to store the result list, which in the worst case can contain all nodes.
---
<a href = "https://leetcode.com/problems/n-ary-tree-postorder-traversal/submissions/1368651449/">![image.png](https://assets.leetcode.com/users/images/5ce5162e-78e7-4994-a602-c278c85719e2_1724655022.7824955.png)</a>
# Code
```python3 []
class Solution:
    def postorder(self, root: 'Node') -> List[int]:
        res = []
        if not root:
            return res
        self.traverse(root,res)
        return res
    def traverse(self, currNode:"Node", post_order: list) -> None:
        if not currNode:
            return
        for child in currNode.children:
            self.traverse(child, post_order)
        post_order.append(currNode.val)
```
---

# Solution 2: DFS
# Intuition  
To perform a postorder traversal of an N-ary tree, our goal is to visit all the child nodes of each node before visiting the node itself. This traversal is particularly useful as it allows processing of child nodes first, which is essential when aggregating or manipulating data hierarchically.  

# Approach  
1. **Initialization**: Create an empty list `res` to store the values in postorder.  
2. **Depth-First Search (DFS)**: Define an inner function `dfs` that accepts a node as its parameter.  
   - **Base Case**: If the node is `None`, return immediately.  
   - **Recursive Traversal**: For each child of the current node, recursively call the `dfs` function to traverse all child nodes.  
   - **Postorder Addition**: After all child nodes have been processed, append the current node's value to the `res` list.  
3. **Call DFS**: Initiate the DFS by calling `dfs(root)`.  
4. **Return Result**: After traversal, return the collected results from the `res` list.  

This structure ensures that we capture the required order of nodes during traversal.  

# Complexity  
- Time complexity: $$O(n)$$, where $$n$$ is the number of nodes in the tree, since each node is visited exactly once.  
- Space complexity: $$O(n)$$ for the recursion stack and the result list, which can grow to contain all nodes in the worst case.
---
<a href = "https://leetcode.com/problems/n-ary-tree-postorder-traversal/submissions/1368654213/">![image.png](https://assets.leetcode.com/users/images/56ce362a-86e1-4b8a-b547-9bc8e58eb290_1724655284.0327058.png)</a>

```python3 []
class Solution:
    def postorder(self, root: 'Node') -> List[int]:
        res = []
        def dfs(node:"Node") -> None:
            if not node:
                return
            for child in node.children:
                dfs(child)
            res.append(node.val)
        dfs(root)
        return res


```
