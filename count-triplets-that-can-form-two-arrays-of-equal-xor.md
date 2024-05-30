## Algorithm

### Problem Statement:
Given an array of integers `arr`, count the number of triplets `(i, j, k)` such that `i < j <= k` and the bitwise XOR of the elements from `arr[i]` to `arr[j-1]` is equal to the bitwise XOR of the elements from `arr[j]` to `arr[k]`.

### Approach:
The problem can be efficiently solved using prefix XOR and a hashmap to keep track of indices where each prefix XOR value has occurred.

1. **Initialize Variables:**
   - `res`: To store the number of valid triplets.
   - `hashmap`: A dictionary to store lists of indices where each prefix XOR value occurs.
   - `cur`: To store the current prefix XOR value.

2. **Iterate Through the Array:**
   - For each element `ele` at index `i` in the array:
     - Update the current prefix XOR value `cur` by XORing it with `ele`.
     - If the current prefix XOR `cur` is `0`, it means the subarray from the start to the current index `i` has a prefix XOR of `0`. This forms valid triplets `(0, j, i)` for all `j` from `1` to `i`.
     - If `cur` is found in the `hashmap`, it means there are subarrays ending before the current index `i` that have the same prefix XOR value. For each index `after` in `hashmap[cur]`, the triplets `(after+1, j, i)` are valid for all `j` from `after+1` to `i`.
     - Add the current index `i` to the list of indices for the current prefix XOR value `cur` in the `hashmap`.

3. **Return the Result:**
   - Return the total number of valid triplets stored in `res`.

# Complexity
- Time complexity: $$O(\ n\ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(\ n\ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
# My Submission
<a href = https://leetcode.com/problems/count-triplets-that-can-form-two-arrays-of-equal-xor/submissions/1272023763/>![image.png](https://assets.leetcode.com/users/images/ba62d353-53ef-47e8-b489-2bc5ade21432_1717044980.1548426.png)</a>
# Code
```
class Solution:
    def countTriplets(self, arr: List[int]) -> int:
        res, hashmap, cur = 0, defaultdict(list), 0
        for i, ele in enumerate(arr):
            cur ^= ele
            if cur == 0:
                res += i
            if cur in hashmap:
                for after in hashmap[cur]:
                    res += (i - after - 1)
            hashmap[cur] += [i]
        return res
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
