# Intuition
- To count the number of fractions smaller than a given fraction, we can iterate through the array and consider all possible pairs of indices `(i, j)` where `i < j`. For each pair, we check if the fraction formed by `arr[i] / arr[j]` is smaller than the given fraction. If it is, we increment the count.

- Since the array is sorted, we notice that if `arr[i] / arr[j]` is smaller than the given fraction, then all subsequent fractions formed by `arr[i] / arr[k]` where`k> j` will also be smaller than the given fraction.

- If we apply the above strategy, the fractions formed by dividing elements at different indices in the sorted array will maintain their sorted order. This enables us to efficiently solve the problem using binary search.

- Now, the key question arises: How can we determine how many fractions are smaller than a given value? Since the array is sorted, we can count fractions by comparing their values against a reference value.

- This reference value can be any fraction between 0 and 1. As the array contains only 1 and prime numbers, we know that all the fractions will be between 0 and 1. Therefore, we can set the initial search range to [0, 1). We initialize two pointers, left and right, representing the lower and upper bounds of the possible fractions.

- We use binary search to iteratively narrow down the search space for the kth smallest fraction. At each step, we calculate the midpoint of the range (`mid`). Using a ***two-pointer approach***, we compare each element of the array to mid and keep a count of how many fractions are smaller than or equal to it. This count helps in evaluating whether to adjust the left or right bounds of our search range and also ensures that we methodically pinpoint the precise kth fraction by reducing the interval based on the number of smaller fractions found.

- However, while iterating through the array, we're also exploring the set of possible fractions, gradually revealing the smallest fractions first. During this exploration, we maintain a record of the maximum fraction encountered so far within the current search range.

- Now, why is this maximum fraction significant? In a sorted array of unique numbers, the fractions increase gradually as we move left to right. If we've encountered k or more fractions smaller than or equal to this maximum fraction, then this maximum fraction is the kth smallest fraction.

- Finally, we adjust the search range based on the count of smaller fractions. If the count equals k, we return the current maximum fraction as the kth smallest fraction. If the count is greater than k, we move the right pointer to mid. Else, we move the left pointer to mid.

# Algorithm
- Initialize the variable `n` to store the size of the input array `arr`. Set `left` to 0 and `right` to 1.0 to establish the initial range for binary search.
- Enter a binary search loop until the left boundary (left) is less than the right boundary (right).
- Calculate the midpoint of the current range, denoted as `mid`, by averaging `left` and `right`.
- Create variables to keep track of key metrics: `maxFraction` to store the maximum fraction encountered, `totalSmallerFractions` to count the number of fractions smaller than `mid`, and `numeratorIdx `and `denominatorIdx` to record the indices of the numerator and denominator of the maximum fraction.
- Initialize `j to 1`, representing the index for the denominator in the array.
- Iterate through the array `arr` to identify fractions smaller than `mid`.
- Increment `j` until the fraction `(arr[i] / arr[j])` is less than or equal to mid, effectively finding the right boundary for the current numerator.
- Increment `totalSmallerFractions` by the count of elements between `j` and `n`.
- Exit the loop if `j` reaches the end of the array `arr`.
- Calculate the fraction `arr[i] / arr[j]` and update `maxFraction`, `numeratorIdx`, and `denominatorIdx` if the calculated fraction exceeds the current maximum fraction.
- Check if `totalSmallerFractions` equals `k`. If it does, return the fraction with the numerator at index `numeratorIdx` and the denominator at index `denominatorIdx`.
- If `totalSmallerFractions` exceeds `k`, update the right boundary of the search range (right) to `mid` to focus on the left portion of the range.
- If `totalSmallerFractions` is less than `k`, update the left boundary of the search range (left) to `mid` to focus on the right portion of the range.
- If the loop concludes without finding the kth smallest prime fraction, return an `empty array`.
# Complexity
- Time complexity: $$O(\ n⋅log(m ^2)\ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O( \ 1\ ) $$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
>Let $$n$$ be the size of the input array and $$m$$ be the maximum value in the array.

# My Submission
<a href = https://leetcode.com/problems/k-th-smallest-prime-fraction/submissions/1254085399/>![image.png](https://assets.leetcode.com/users/images/c6221928-b54e-4d3c-bc92-d662b76d7470_1715312839.4656641.png)</a>

---


# Let's Code it down
```
class Solution:
    def kthSmallestPrimeFraction(self, arr, k):
        n = len(arr)
        left, right = 0, 1.0
        
        # Binary search for finding the kth smallest prime fraction
        while left < right:
            # Calculate the middle value
            mid = (left + right) / 2
            # Initialize variables to keep track of maximum fraction and indices
            max_fraction = 0.0
            total_smaller_fractions = 0
            numerator_idx, denominator_idx = 0, 0
            j = 1
            
            # Iterate through the array to find fractions smaller than mid
            for i in range(n - 1):
                while j < n and arr[i] >= mid * arr[j]:
                    j += 1

                # Count smaller fractions
                total_smaller_fractions += (n - j)

                # If we have exhausted the array, break
                if j == n:
                    break

                # Calculate the fraction
                fraction = arr[i] / arr[j]

                # Update max_fraction and indices if necessary
                if fraction > max_fraction:
                    numerator_idx = i
                    denominator_idx = j
                    max_fraction = fraction

            # Check if we have found the kth smallest prime fraction
            if total_smaller_fractions == k:
                return [arr[numerator_idx], arr[denominator_idx]]
            elif total_smaller_fractions > k:
                right = mid  # Adjust the range for binary search
            else:
                left = mid  # Adjust the range for binary search
                
        return []  # Return empty list if kth smallest prime fraction not found
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)

