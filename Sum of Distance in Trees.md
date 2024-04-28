# My submission
<a href = https://leetcode.com/problems/sum-of-distances-in-tree/submissions/1243843048/>![Screenshot 2024-04-28 094604.png](https://assets.leetcode.com/users/images/11d5cceb-60ba-4272-bf9d-76d560ea8e85_1714277794.8453228.png)</a>

# Complexity
- Time complexity: $$O(\ n\ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(\ n\ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution:
  def sumOfDistancesInTree(self, n: int, edges: List[List[int]]) -> List[int]:
    ans = [0] * n
    count = [1] * n
    tree = collections.defaultdict(set)

    for u, v in edges:
      tree[u].add(v)
      tree[v].add(u)

    def postorder(node, parent=None):
      for child in tree[node]:
        if child == parent:
          continue
        postorder(child, node)
        count[node] += count[child]
        ans[node] += ans[child] + count[child]

    def preorder(node, parent=None):
      for child in tree[node]:
        if child == parent:
          continue
        # count[child] nodes are 1 step closer from child than parent.
        # (n - count[child]) nodes are 1 step farther from child than parent.
        ans[child] = ans[node] - count[child] + (n - count[child])
        preorder(child, node)

    postorder(0)
    preorder(0)
    return ans
```
