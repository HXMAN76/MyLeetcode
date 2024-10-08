# Intuition  
The problem requires us to determine the minimum number of swaps needed to balance a string of brackets, specifically square brackets `[` and `]`. A balanced string means that every opening bracket `[` has a corresponding closing bracket `]` and they are in the correct order. Initially, I thought about counting the number of unmatched brackets and then calculating how many swaps would be necessary to correct them.  

# Approach  
To solve this problem, I will iterate through the string while maintaining two counters: `opening` for the number of unmatched opening brackets `[` and `unbalanced` for the number of unmatched closing brackets `]`. As I traverse the string:  

1. If I encounter an opening bracket `[`, I increment the `opening` counter.  
2. If I encounter a closing bracket `]` and there is an unmatched opening bracket (i.e., `opening > 0`), I decrement the `opening` counter because this closing bracket can match with one of the opening brackets.  
3. If I encounter a closing bracket `]` and there are no unmatched opening brackets (i.e., `opening == 0`), I increment the `unbalanced` counter because this closing bracket is unmatched.  

At the end of the traversal, the number of swaps needed to balance the brackets can be calculated as the total unmatched closing brackets divided by 2 (since each swap can fix two unbalanced brackets). If there is an odd number of unmatched brackets, we add one more swap to account for the last unmatched bracket.  

# Complexity  
- Time complexity: $$O(n)$$, where $$n$$ is the length of the string, as we are iterating through the string once.  
- Space complexity: $$O(1)$$, since we are using a constant amount of space for the counters.
---
<a href = https://leetcode.com/problems/minimum-number-of-swaps-to-make-the-string-balanced/submissions/1415776452/>![image.png](https://assets.leetcode.com/users/images/69a319ce-eeab-44d0-8bda-72524baafa7d_1728385487.9069424.png)</a>
# Code
```java []
class Solution {
    public int minSwaps(String s) {
        int opening = 0;
        int unbalanced = 0;

        for (var c: s.getBytes()) {
            if (c == '[') {
                opening++;
            } else {
                if (opening > 0)
                    opening--;
                else
                    unbalanced++;    
            }
        }

        return unbalanced / 2 + unbalanced % 2;
    }
}
```
