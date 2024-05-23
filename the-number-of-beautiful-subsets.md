## Algorithm:

### Function: `beautifulSubsets`
1. **Initialization:**
   - Initialize `count` to 1 (to account for the multiplication logic later).
   - Create a nested dictionary `freq` using `defaultdict` to store the frequency of numbers based on their modulus with `k`.

2. **Frequency Calculation:**
   - For each number `num` in the input list `nums`, update the `freq` dictionary. Group numbers by their modulus with `k`, and count occurrences.

3. **Count Beautiful Subsets:**
   - For each group of numbers in `freq`:
     - Sort the numbers and convert them into a list of tuples `subsets` where each tuple contains a number and its frequency.
     - Multiply `count` by the result of `count_beautiful_subsets` function called with `subsets`, the length of `subsets`, `k`, and starting index `0`.

4. **Return Result:**
   - Subtract 1 from `count` to exclude the empty set.
   - Return `count`.

### Function: `count_beautiful_subsets`
1. **Base Case:**
   - If the index `i` equals `num_subsets`, return 1.

2. **Recursive Case:**
   - Calculate the number of subsets where the current element is not included by calling `count_beautiful_subsets` with the next index 
(`i + 1`).
   - Calculate the number of subsets where the current element is included:
        - Initialize `take` with the total combinations of the current subset (using bitwise left shift).
        - If the next element exists and has the required difference (`diff`), recursively calculate the subsets skipping the next element
        (`i + 2`).
        - Otherwise, recursively calculate the subsets including the next element (`i + 1`).

3. **Return Total:**
   - Return the sum of `skip` and `take`.

## Time Complexity:
- The time complexity is $$O(2^n)$$

## Space Complexity:
- The space complexity is $$O(n)$$ for the frequency dictionary and recursion stack.
---
## My Submission
<a href = https://leetcode.com/problems/the-number-of-beautiful-subsets/submissions/1265436497/>![image.png](https://assets.leetcode.com/users/images/ffb0a0c3-db17-464e-8ed7-ba5fdef72163_1716439670.9037528.png)</a>
## Code:
```python
class Solution:
    def beautifulSubsets(self, nums: List[int], k: int) -> int:
        count = 1
        freq = defaultdict(lambda: defaultdict(int))
        for num in nums:
            freq[num % k][num] += 1
        
        for fr in freq.values():
            subsets = sorted(fr.items())
            count *= self.count_beautiful_subsets(subsets, len(subsets), k, 0)
        return count - 1 # Subtract one empty set

    def count_beautiful_subsets(self, subsets, num_subsets, diff, i):
        if i == num_subsets:
            return 1
        # Calculate subsets where the current subset is not taken
        skip = self.count_beautiful_subsets(subsets, num_subsets, diff, i + 1)
        # Calculate subsets where the current subset is taken
        take = (1 << subsets[i][1]) - 1
        # If next number has a 'difference', calculate subsets; otherwise, move to next
        if i + 1 < num_subsets and subsets[i + 1][0] - subsets[i][0] == diff:
            take *= self.count_beautiful_subsets(subsets, num_subsets, diff, i + 2)
        else:
            take *= self.count_beautiful_subsets(subsets, num_subsets, diff, i + 1)
        return skip + take # Total count of only beautiful subsets

```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
