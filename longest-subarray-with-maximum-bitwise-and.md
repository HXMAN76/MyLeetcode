
# Intuition
To solve the problem of finding the longest subarray containing the maximum element, my first thought is to identify the maximum value in the array, as this will be the target for our subarray. Once we have the maximum value, we can iterate through the array to count the length of consecutive occurrences of this maximum value.

# Approach
1. **Find the Maximum Value:** Iterate through the array to determine the maximum value.
2. **Count Consecutive Occurrences:** Iterate through the array again, counting how many times the maximum value appears consecutively. Keep track of the longest sequence found during this iteration.
3. **Return the Count:** After completing the iterations, return the length of the longest sequence of the maximum value.

This approach ensures that we efficiently find the desired subarray with a minimal number of passes through the data.

# Complexity
- Time complexity: $$O(n)$$
- Space complexity: $$O(1)$$
---
<a href = https://leetcode.com/problems/longest-subarray-with-maximum-bitwise-and/submissions/1389532775/>![image.png](https://assets.leetcode.com/users/images/57a80489-9c1c-4019-ace6-de628956276b_1726298588.5672753.png)</a>

# Code
```java []
class Solution {
    public int longestSubarray(int[] a) {
        int n = a.length, max = 0, count = 0, count1 = 0;
        for(int i = 0 ; i < n ; i++)
        {
            if(max < a[i]) {
                max = a[i];
            }
        }
        for(int i = 0; i < n; i++)
        {
            if(max == a[i]) {
                count1++;
                count = Math.max(count, count1);
            }
            else {
                count1=0;
            }
            
        }
        return count;
        
    }
}
```
