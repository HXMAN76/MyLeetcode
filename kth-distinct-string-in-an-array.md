# Approach
<!-- Describe your approach to solving the problem. -->
**1. Purpose of Counter:**
    In Python, a Counter is a subclass of the dict class from the collections module that helps count hashable objects. It is commonly used to count occurrences of elements in an iterable. You can create a Counter by passing an iterable or a dictionary of counts to it.
**2. Logic in code:**
    The logic in code is very simple after creating the counter object which is done in $$ O(n) $$ , We iterate through the `arr` to find the distinct elements and minus the `k` whenever we find one till it becomes zero. If this element is not founnd then we simple return a empty string
# Complexity
- Time complexity: $$ O(n) $$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$ O(n) $$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution:
    def kthDistinct(self, arr: List[str], k: int) -> str:
        res = Counter(arr)
        for i in arr:
            if res[i] == 1:
                k -= 1
                if k == 0:
                    return i
        return ""    
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
