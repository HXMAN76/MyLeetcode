# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
To be isomorphic the strings must be in same length and the mapping of the string must be the same, which means like the concept of the inverse of a function in which the domains of a function is switched to co-domain and vise-versa , The mapping of each string should be same when its reversed 
# Approach
<!-- Describe your approach to solving the problem. -->
**STEP 1** - Create two dictionaries and iterate the strings to append the dictionaries such that one dictionary contains the first string's character as keys whereas the other string makes that as a values.
**STEP 2** - While creating these dictionaries we can get errors if the given string is not isomorphic then same keys can get multiple values hence we just add 'if' statements and end the function by returning the boolean value False

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution(object):
    def isIsomorphic(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        if len(s) != len(t):
            #if length of strings or not same then its not isomorphic
            return False
        #dictionary that hold characters of s as keys and characters of t as values
        chars = {}
        for i in range(len(s)):
            if s[i] in chars:
                if t[i] == chars[s[i]]:
                    continue
                else:
                    #if same key as two different value then its not isomorphic
                    return False
            else:
                chars[s[i]] = t[i]
        #reversing the dictionary to make values into keys and keys into values
        reverse_char={}
        for key,val in chars.items():
            if val in reverse_char:
                if key == reverse_char[val]:
                    continue
                else:
                    return False
            else:
                reverse_char[val] = key

        return True
```
