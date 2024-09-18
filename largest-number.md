# Intuition

The intuition behind this problem is to find the largest number that can be formed by concatenating the given integers. To achieve this, we need to sort the integers based on their concatenated values in descending order.

# Approach

1. Convert each integer to a string and store them in an array.
2. Sort the array of strings based on the concatenated values of the strings in descending order.
3. If the first element of the sorted array is "0", return "0" as the largest number.
4. Concatenate the sorted strings to form the largest number.

The key to solving this problem is the custom comparator used in the sorting step. The comparator compares two strings `a` and `b` based on the concatenation of `b + a` and `a + b`. If `(b + a)` is lexicographically greater than `(a + b)`, it means that `b` should come before `a` in the sorted order.

## Example

Let's say we have the input `nums = [3, 30, 34, 5, 9]`.

1. Convert integers to strings: `["3", "30", "34", "5", "9"]`.
2. Sort the array using the custom comparator: `["9", "5", "34", "3", "30"]`.
3. Since the first element is not "0", concatenate the sorted strings: `"95334330"`.

# Complexity

- Time complexity: $$O(n \log n)$$, where $$n$$ is the length of the input array. The time complexity is dominated by the sorting step, which takes $$O(n \log n)$$ time.
- Space complexity: $$O(n)$$, where $$n$$ is the length of the input array. We create an array of strings to store the input integers, which requires $$O(n)$$ space.
---
<a href = https://leetcode.com/problems/largest-number/submissions/1394284052/>![image.png](https://assets.leetcode.com/users/images/7835327a-881c-45ca-af93-835cfa63ec31_1726659093.1090603.png)</a>

# Code
```java []
class Solution {

    public String largestNumber(int[] nums) {
        // Convert each integer to a string
        String[] numStrings = new String[nums.length];
        for (int i = 0; i < nums.length; i++) {
            numStrings[i] = Integer.toString(nums[i]);
        }

        // Sort strings based on concatenated values
        Arrays.sort(numStrings, (a, b) -> (b + a).compareTo(a + b));

        // Handle the case where the largest number is zero
        if (numStrings[0].equals("0")) {
            return "0";
        }

        // Concatenate sorted strings to form the largest number
        StringBuilder largestNum = new StringBuilder();
        for (String numStr : numStrings) {
            largestNum.append(numStr);
        }

        return largestNum.toString();
    }
}
```
