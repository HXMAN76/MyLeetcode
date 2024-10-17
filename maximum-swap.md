# Intuition  
The problem requires us to maximize a number by swapping two digits at most once. To achieve this, we need to identify the rightmost digit that can be swapped with a larger digit to its right. The goal is to find the first smaller digit when traversing the number from right to left and then swap it with the largest digit found to its right. This way, we can ensure that the resulting number is maximized.  

# Approach  
1. Convert the number to a character array to facilitate digit manipulation.  
2. Traverse the array from right to left, keeping track of the maximum digit encountered so far and its index.  
3. Whenever a smaller digit is found (compared to the maximum digit), mark these indices for a potential swap.  
4. After the traversal, if valid indices for swapping are found, perform the swap.  
5. Convert the character array back to an integer and return it.  

This approach ensures that we only make one pass through the digits, making it efficient.  

# Complexity  
- Time complexity: $$O(n)$$, where $$n$$ is the number of digits in the number since we traverse the digits once.  
- Space complexity: $$O(n)$$, for storing the character array representation of the number.
---
<a href = https://leetcode.com/problems/maximum-swap/submissions/1425273477/>![image.png](https://assets.leetcode.com/users/images/79548ad0-ed86-4866-81d2-a3323a0575d9_1729162720.2279425.png)</a>

# Code
```java []
class Solution {

    public int maximumSwap(int num) {
        char[] numStr = Integer.toString(num).toCharArray();
        int n = numStr.length;
        int maxDigitIndex = -1, swapIdx1 = -1, swapIdx2 = -1;

        // Traverse the string from right to left, tracking the max digit and
        // potential swap
        for (int i = n - 1; i >= 0; --i) {
            if (maxDigitIndex == -1 || numStr[i] > numStr[maxDigitIndex]) {
                maxDigitIndex = i; // Update the index of the max digit
            } else if (numStr[i] < numStr[maxDigitIndex]) {
                swapIdx1 = i; // Mark the smaller digit for swapping
                swapIdx2 = maxDigitIndex; // Mark the larger digit for swapping
            }
        }

        // Perform the swap if a valid swap is found
        if (swapIdx1 != -1 && swapIdx2 != -1) {
            char temp = numStr[swapIdx1];
            numStr[swapIdx1] = numStr[swapIdx2];
            numStr[swapIdx2] = temp;
        }

        return Integer.parseInt(new String(numStr)); // Return the new number or the original if no
        // swap occurred
    }
}
```
