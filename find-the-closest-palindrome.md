
# Intuition  
The problem requires finding the nearest palindrome to a given number. A palindrome is a number that reads the same forwards and backwards. The first thought is to generate possible palindrome candidates by manipulating the digits of the given number. This involves considering both the next larger palindrome and the previous smaller palindrome, as the closest palindrome could be either.  

# Approach  
1. **Convert Function**: This function generates a palindrome by mirroring the left half of the number onto the right half. It handles both even and odd-length numbers by adjusting the indices accordingly.  
  
2. **Next Palindrome**: This function uses binary search to find the smallest palindrome greater than the given number. It checks the mid-point's palindrome and adjusts the search range based on whether the found palindrome is less than or greater than the target number.  

3. **Previous Palindrome**: Similar to the next palindrome function, this function finds the largest palindrome less than the given number using binary search.  

4. **Nearest Palindromic**: This function compares the distances from the given number to both the next and previous palindromes found in the previous steps. It returns the closest one as a string.  

# Complexity  
- Time complexity: $$O(n \log n)$$, where $$n$$ is the number of digits in the input number. The log factor comes from the binary search approach used to find the next and previous palindromes.  
  
- Space complexity: $$O(n)$$, due to the string manipulation and storage of palindrome candidates.

---

<a href = https://leetcode.com/problems/find-the-closest-palindrome/submissions/1366443148/>![image.png](https://assets.leetcode.com/users/images/0574729f-34e7-42f7-9806-bb6549b9534e_1724484283.3452008.png)</a>


# Code
```python3 []
class Solution:
    def convert(self, num: int) -> int:
            s = str(num)
            n = len(s)
            left, right = (n-1) // 2 , n // 2
            arr = list(s)
            while left >= 0:
                arr[right] = arr[left]
                right += 1
                left -= 1
            return int("".join(arr))
    def nextPalindrome(self, num: int) -> int:
        left , right = 0, num
        ans = float("-inf")
        while left <= right:
            mid = (right - left) // 2 + left
            p = self.convert(mid)
            if p < num:
                ans = p
                left = mid + 1
            else:
                right = mid - 1
        return ans
    def prevPalindrome(self, num: int) -> int:
        left , right = num , int(1e18)
        ans = float("-inf")
        while left <= right:
            mid = (right - left) // 2 + left
            p = self.convert(mid)
            if p > num:
                ans = p
                right = mid - 1
            else:
                left = mid + 1 
        return ans

    def nearestPalindromic(self, n: str) -> str:
        num = int(n)
        a = self.nextPalindrome(num)
        b = self.prevPalindrome(num)
        if abs(a - num) <= abs(b - num):
            return str(a)
        else:
            return str(b)       
```
# Note:
there is another solution in leetcode which is better...
