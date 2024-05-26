## Algorithm:

## Problem Statement:
Given an integer `n`, return the number of possible attendance records of length `n` that do not contain more than one 'A' (absent) and no more than two continuous 'L' (late).

## Approach:
The solution uses matrix exponentiation to efficiently calculate the number of valid attendance records. The main idea is to represent the state transitions of the attendance records using matrix multiplication.

### Steps:
1. **Define Constants and Helper Functions:**
   - Define `MOD` to be \(10^9 + 7\) to ensure results fit within standard integer limits.
   - Implement `matmul(A, B)` for matrix multiplication.
   - Implement `pow(A, n)` for matrix exponentiation.

2. **State Representation:**
   - Use a 6x6 matrix to represent state transitions.
   - The states are defined as follows:
     - `S0`: No 'A' and ends with 'P'.
     - `S1`: No 'A' and ends with one 'L'.
     - `S2`: No 'A' and ends with two 'L's.
     - `S3`: One 'A' and ends with 'P'.
     - `S4`: One 'A' and ends with one 'L'.
     - `S5`: One 'A' and ends with two 'L's.

3. **Matrix Exponentiation:**
   - Use matrix exponentiation to compute the number of valid attendance records in O(log n) time.

4. **Initial Transition Matrix:**
   - Define the transition matrix `A` to represent state transitions.

5. **Calculate Result:**
   - Compute the matrix power of `A` to the power of `n`.
   - Sum up the first column of the resulting matrix to get the total number of valid sequences.
# My submission
<a href = https://leetcode.com/problems/student-attendance-record-ii/submissions/1268203477/>![image.png](https://assets.leetcode.com/users/images/2e71fd30-87ae-4b02-9652-23a34b08d939_1716701204.4881938.png)</a>
## Let's Code it down:
```python
class Solution:
    def checkRecord(self, n: int) -> int:
        
        MOD = int(1e9+7)

        def matmul(A, B):
            C = [[0 for _ in range(6)] for _ in range(6)]
            for k in range(6):
                for i in range(6):
                    for j in range(6): C[i][j] = (C[i][j]+A[i][k]*B[k][j])%MOD
            return C
        
        def pow(A, n):
            if n==1: return A
            
            t = pow(A, int(n/2))
            t = matmul(t, t)

            if (n%2)==0: return t
            else: return matmul(A, t)
        
        t = pow([[1, 1, 1, 0, 0, 0], [1, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0], [1, 1, 1, 1, 1, 1], [0, 0, 0, 1, 0, 0], [0, 0, 0, 0, 1, 0]], n)
        
        return sum([t[i][0] for i in range(6)])%MOD
        
```
## Same code for easy understanding
```python
class Solution:
    def checkRecord(self, n: int) -> int:
        
        MOD = int(1e9 + 7)

        def matmul(A, B):
            C = [[0 for _ in range(6)] for _ in range(6)]
            for k in range(6):
                for i in range(6):
                    for j in range(6): 
                        C[i][j] = (C[i][j] + A[i][k] * B[k][j]) % MOD
            return C
        
        def pow(A, n):
            if n == 1:
                return A
            
            t = pow(A, n // 2)
            t = matmul(t, t)

            if n % 2 == 0:
                return t
            else:
                return matmul(A, t)
        
        # Transition matrix for state changes
        transition_matrix = [
            [1, 1, 1, 0, 0, 0],
            [1, 0, 0, 0, 0, 0],
            [0, 1, 0, 0, 0, 0],
            [1, 1, 1, 1, 1, 1],
            [0, 0, 0, 1, 0, 0],
            [0, 0, 0, 0, 1, 0]
        ]
        
        # Matrix exponentiation
        result_matrix = pow(transition_matrix, n)
        
        # Sum the first column of the result matrix
        return sum(result_matrix[i][0] for i in range(6)) % MOD
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
