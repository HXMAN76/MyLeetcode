# Intuition  
The problem requires us to evaluate a string representation of a series of fractions and return the result as a simplified fraction. The key is to handle the addition of fractions properly, which involves finding a common denominator and summing the numerators accordingly. The final result should be simplified using the greatest common divisor (GCD).  

# Approach  
1. **Parsing the Expression**: We can use regular expressions to split the input string into numerators and denominators. The fractions are separated by '+' or '-' signs, so we need to account for that while parsing.  
   
2. **Initialization**: We start with a numerator (`num`) of 0 and a denominator (`denom`) of 1, representing the fraction 0/1.  

3. **Iterating Through Fractions**: For each fraction in the parsed list:  
   - Convert the numerator and denominator into integers.  
   - Update the overall numerator and denominator using the formula for adding fractions:  
   - \[ `num` = `num` * `curr_denom` + `curr_num` * `denom`  \]  
   - \[  ``denom`` = `denom` * `curr_denom`  \]  
   
4. **Simplifying the Result**: After processing all fractions, compute the GCD of the final numerator and denominator to simplify the fraction.  

5. **Returning the Result**: Format the result as a string in the form "numerator/denominator".  

# Complexity  
- Time complexity: $$O(n)$$ where \(n\) is the number of characters in the input string. This accounts for parsing the string and iterating through the fractions.  
  
- Space complexity: $$O(n)$$ for storing the list of parsed numerators and denominators.

---
<a href = https://leetcode.com/problems/fraction-addition-and-subtraction/submissions/1365462711/>![image.png](https://assets.leetcode.com/users/images/b6daa5be-5506-4a98-9263-c6c07395e507_1724398664.2129157.png)</a>

# Code
```python3 []
class Solution:
    def fractionAddition(self, expression: str) -> str:
        def FindGCD(a, b):  
            if b == 0:  
                return a  
            else:  
                return FindGCD(b, a % b)
        num = 0
        denom = 1

        nums = re.split("/|(?=[-+])",expression)
        nums = list(filter(None, nums))

        for i in range(0, len(nums), 2):
            curr_num = int(nums[i])
            curr_denom = int(nums[i + 1])

            num = num * curr_denom + curr_num * denom
            denom *= curr_denom
        gcd = abs(FindGCD(num, denom))
        num //= gcd 
        denom //= gcd
        return str(num) + "/" + str(denom)
        
```
