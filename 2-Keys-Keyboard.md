
# Complexity
- Time complexity: $$O(√n)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(1)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```python3 []
class Solution:
    def minSteps(self, n: int) -> int:
        if n == 1:
            return 0 
        step = 0
        fact = 2
        while n > 1:
            while n % fact == 0:
                step += fact
                n //= fact
            fact +=1
        return step
        
```
