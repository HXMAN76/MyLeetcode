# Intuition  
To solve the problem of finding the minimum number of groups required to accommodate overlapping intervals, we need to track how many intervals are active at any given point. The main challenge is to efficiently manage the start and end of these intervals to determine the maximum number of overlapping intervals at any point in time.  

# Approach  
1. **Identify the Range**: First, we determine the minimum start and maximum end of the intervals to establish the range of points we need to analyze.  
2. **Use a Difference Array**: We create a difference array (`pointToCount`) to mark the start and end of each interval. For each interval, we increment the count at the starting point and decrement it right after the ending point.  
3. **Calculate Active Intervals**: We then iterate through the difference array to compute the number of active intervals at each point. By maintaining a cumulative sum, we can track how many intervals are overlapping at any given point.  
4. **Find the Maximum**: The maximum value of active intervals during this iteration will give us the minimum number of groups required.  

# Complexity  
- Time complexity: $$O(n)$$, where $$n$$ is the number of intervals, since we process each interval a constant number of times.  
- Space complexity: $$O(m)$$, where $$m$$ is the range of values from the minimum start to the maximum end of the intervals. This space is used for the difference array.
---
<a href = https://leetcode.com/problems/divide-intervals-into-minimum-number-of-groups/submissions/1419756308/>![image.png](https://assets.leetcode.com/users/images/a2456686-8ed0-4b14-8408-ba6be0f1344d_1728722511.140728.png)</a>

# Code
```java []
class Solution {

    public int minGroups(int[][] intervals) {
        // Find the minimum and maximum value in the intervals
        int rangeStart = Integer.MAX_VALUE;
        int rangeEnd = Integer.MIN_VALUE;
        for (int[] interval : intervals) {
            rangeStart = Math.min(rangeStart, interval[0]);
            rangeEnd = Math.max(rangeEnd, interval[1]);
        }

        // Initialize the array with all zeroes
        int[] pointToCount = new int[rangeEnd + 2];
        for (int[] interval : intervals) {
            pointToCount[interval[0]]++; // Increment at the start of the interval
            pointToCount[interval[1] + 1]--; // Decrement right after the end of the interval
        }

        int concurrentIntervals = 0;
        int maxConcurrentIntervals = 0;
        for (int i = rangeStart; i <= rangeEnd; i++) {
            // Update currently active intervals
            concurrentIntervals += pointToCount[i];
            maxConcurrentIntervals = Math.max(
                maxConcurrentIntervals,
                concurrentIntervals
            );
        }

        return maxConcurrentIntervals;
    }
}
```
