# Intuition  
My initial thought on solving the problem is to recognize that the task is to minimize the number of turns needed to print a string where consecutive characters are the same. This means that if we can reduce the string by merging identical characters, we can potentially minimize the number of turns needed. The problem can be approached using dynamic programming, where we recursively calculate the minimum turns required for different segments of the string.  

# Approach  
1. **Reduce the Problem**: First, we can simplify the string by removing consecutive duplicate characters. This will help in reducing the complexity of the problem since we will only deal with unique characters that change.  
  
2. **Dynamic Programming**: We will use a recursive function with memoization to calculate the minimum number of turns needed to print the string from index `start` to `end`. The base case will be when `start` is greater than `end`, returning 0.  

3. **Recursion Logic**:  
   - Start with the worst-case scenario where we assume we need to make a turn for each character, which would be `1 + min_turns(start + 1, end)`.  
   - For every character from `start + 1` to `end`, if the character matches `s[start]`, we can potentially reduce the number of turns by combining the segments. We will calculate the turns needed for the left segment (`start` to `k-1`) and the right segment (`k + 1` to `end`), and update our minimum accordingly.  

4. **Memoization**: Store the results of computed segments in a dictionary to avoid redundant calculations and speed up the process.  

5. **Final Output**: The result of the function will be the minimum number of turns needed to print the entire string.  

# Complexity  
- Time complexity: $$O(n^3)$$, where `n` is the length of the reduced string. This is due to the nested loops for calculating the minimum turns across segments.  
  
- Space complexity: $$O(n)$$ for the memoization dictionary, which stores results for segments of the string.

---


<a href = "https://leetcode.com/problems/strange-printer/submissions/1363159848/">![image.png](https://assets.leetcode.com/users/images/adca7de4-a5a4-44ad-9fdb-d04f27e0d43b_1724220269.0276392.png)</a>

# Code
```python3 []
class Solution:
    def strangePrinter(self, s: str) -> int:
        s = "".join(char for char, _ in itertools.groupby(s))
        memo = {}
        def min_turns(start , end) -> int:
            if start > end:
                return 0
            if (start , end) in memo:
                return memo[(start,end)]
            #Worst case
            min_ = 1 + min_turns(start + 1, end)

            for k in range(start + 1, end + 1):
                if s[k] == s[start]:
                    turns_with_match = min_turns(start,k-1) + min_turns(k + 1, end)
                    min_ = min(min_ , turns_with_match)
            
            memo[(start,end)] = min_
            return min_
        return min_turns(0, len(s) - 1)
```
