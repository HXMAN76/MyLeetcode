# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
To approch this kind of problem we can apply `DFS - Depth first Search` this method is used to track the deepest node and we can apply connditions to make the algorithm to solve our problem.

---


# Approach
<!-- Describe your approach to solving the problem. -->
1. Create a seperate function dfs with arguments `root` - the tree  , `path`- to track all the visited nodes till leaf node is found and `smallest`- to find the smallest charecter in lexical order
2. Base conditions: if root is null return , if leaf node is found reverse the path list and convert to a `string` and  compare with `smallest` to find the proper lexical character.
3. Also append the val of each root into path by converting into a character. 
4. Recursively call the functions and pop the last character from path.
5. In the `smallestFromLeaf` create `smallest` variable with the highest lexical character and pass it through dfs and return the `smallest[0]` which contains the smallest lexical ordered character possible

---

# Complexity
- Time complexity: $$O( \ n \ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(\ h \ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
Where `n` is number of nodes and `h` is height of the tree. 
# My submission
<a href= "https://leetcode.com/problems/smallest-string-starting-from-leaf/submissions/1234558533/?envType=daily-question&envId=2024-04-17">![Screenshot 2024-04-17 102805.png](https://assets.leetcode.com/users/images/73122cd6-8670-4e62-95e0-8a1a1f316e3c_1713331032.8762429.png)
</a>


---


# Let's Code
```
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def dfs(self,root, path, smallest):
        #base case
        if not root:
            return
        
        path.append(chr(ord('a') + root.val))
        
        #base case
        if root.left is None and root.right is None:
            current_string = "".join(path[::-1])
            smallest[0] = min(current_string, smallest[0])
        
        #recursive call
        self.dfs(root.left, path, smallest)
        self.dfs(root.right,path,smallest)
        
        #backtrack : removing the current node's character from path
        path.pop()
                
    def smallestFromLeaf(self, root):
        """
        :type root: TreeNode
        :rtype: str
        """
        #intialising the smallest string with largest value possible
        smallest = [chr(ord('z') + 1)]

        self.dfs(root, [], smallest)

        return smallest[0]       
```
![Upvote img](https://i.imgflip.com/28rbtl.jpg)
> ***Have a nice day...***
