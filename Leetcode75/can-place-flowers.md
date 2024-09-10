
# Can Place Flowers Solution

## Intuition
The problem requires us to determine if we can plant `n` flowers in a flowerbed without violating the rule that no two flowers can be planted in adjacent plots. The first thought is to iterate through the flowerbed and check for suitable spots where flowers can be planted.

## Approach
1. **Initialization**: Start with a counter `res` to keep track of the number of flowers that can be planted and an index `i` to traverse the flowerbed.
2. **Iterate through the flowerbed**:
   - If the current plot (`flowerbed[i]`) is `1`, it means a flower is already planted, so skip to the next possible plot by increasing `i` by `2`.
   - If `i` is `0` (the first plot):
     - If the flowerbed has only one plot, plant a flower if it's empty.
     - If the next plot is empty (`flowerbed[i+1]`), plant a flower and skip to the next possible plot.
   - If `i` is the last index:
     - Check if the previous plot is empty before planting a flower.
   - For all other plots:
     - Check if both adjacent plots (previous and next) are empty before planting.
3. **Return Result**: After iterating through the flowerbed, compare the count of planted flowers (`res`) with `n`. If `res` is greater than or equal to `n`, return `true`; otherwise, return `false`.

## Complexity
- **Time complexity**: $$O(n)$$ - We traverse the flowerbed array once.
- **Space complexity**: $$O(1)$$ - We use a constant amount of space for variables.
---
<a href = https://leetcode.com/problems/can-place-flowers/submissions/1385539449/>![image.png](https://assets.leetcode.com/users/images/ee537db9-c956-4763-a6fe-f94432690ec6_1725983047.8288052.png)</a>

# Code
```java []
class Solution {
    public boolean canPlaceFlowers(int[] flowerbed, int n) {
        //this is can be broke down into n cases.
        int res = 0;
        int i = 0;
        int length = flowerbed.length;
        while (i < length){
            if (flowerbed[i] == 1){
                //can't plant adjacent
                //skip 2 index
                i = i + 2;
                continue;
            }
            if (i == 0){
                if (length == 1){
                    res++;
                    i++;
                    continue;
                }
                if (flowerbed[i+1] == 0){
                    //count will be appended and index skips by 2
                    res++;
                    i = i + 2;
                    continue; 
                }
                else{
                    i = i + 2;
                    continue;
                }
            }

            if (i == length - 1) {
                if (flowerbed[i - 1] == 0) {
                    res++;
                    i++;
                    continue;
                }
            }

            if (flowerbed[i-1] == 0 && flowerbed[i+1] == 0) {
                res++;
                i = i + 2;
                continue;
            }
            i++;
        }
        return res >= n;
    }
}
```
