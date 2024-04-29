# Complexity
- Time complexity: $$O(\ n\ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(\ 1\ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

<a href=https://leetcode.com/problems/minimum-number-of-operations-to-make-array-xor-equal-to-k/submissions/1244702228/>![image.png](https://assets.leetcode.com/users/images/7a16e6f2-a90d-4417-9cac-adeb8b5a15d9_1714372748.472732.png)</a>

# Lets code it down
```
from typing import List


class Solution:
    def minOperations(self, nums: List[int], k: int) -> int:
        temp = 0
        for i in nums:
            temp ^= i
        temp ^= k
        return bin(temp).count('1')
```
# method 2
```
class Solution:
    def minOperations(self, nums: List[int], k: int) -> int:
        final_xor = 0
        # XOR of all integers in the array.
        for n in nums:
            final_xor = final_xor ^ n

        count = 0
        # Keep iterating until both k and final_xor becomes zero.
        while k or final_xor:
            # k % 2 returns the rightmost bit in k,
            # final_xor % 2 returns the rightmost bit in final_xor.
            # Increment counter, if the bits don't match.
            if (k % 2) != (final_xor % 2):
                count += 1

            # Remove the last bit from both integers.
            k //= 2
            final_xor //= 2

        return count
```
