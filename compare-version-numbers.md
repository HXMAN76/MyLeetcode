# Algorithm 
1. Convert the version1 and version2 into list of integers.
2. Iterate the list of intgers v1 and v2 using zip_longest
3. Check for each integers and return 1 and -1.
4. if no difference return 0.

***NOTE :***
> The Itertools.zip_longest () This iterator falls under the category of Terminating Iterators. It prints the values of iterables alternatively in sequence. If one of the iterables is printed fully, the remaining values are filled by the values assigned to fillvalue parameter. Syntax: zip_longest(iterable1, iterable2, fillval)
# Complexity
- Time complexity: $$O(\ n\ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(\ n\ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# My submission
<a href = https://leetcode.com/problems/compare-version-numbers/submissions/1247926723/>![image.png](https://assets.leetcode.com/users/images/c8f0b0e0-a3c3-4e89-b50c-d51c605186de_1714709651.744742.png)</a>

# Lets Code it down
```
class Solution:
    def compareVersion(self, version1: str, version2: str) -> int:

        def preprocess(version: str):
            # conversion from string to list of integers
            return map(int, version.split("."))
        
        v1 = preprocess(version1)
        v2 = preprocess(version2)

        for x1, x2 in zip_longest(v1, v2, fillvalue=0):
            if x1>x2:
                return 1
            if x1<x2:
                return -1
        
        return 0
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
