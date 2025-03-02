Location: https://leetcode.com/problems/n-th-tribonacci-number/description/?envType=study-plan-v2&envId=leetcode-75
# Question
The Tribonacci sequence Tn is defined as follows: 

T0 = 0, T1 = 1, T2 = 1, and Tn+3 = Tn + Tn+1 + Tn+2 for n >= 0.

Given n, return the value of Tn.

# Example

## Example 1:

Input: n = 4

Output: 4

Explanation: 
</br>T_3 = 0 + 1 + 1 = 2
</br>T_4 = 1 + 1 + 2 = 4

## Example 2:

Input: n = 25

Output: 1389537

Constraints:

- 0 <= n <= 37
- The answer is guaranteed to fit within a 32-bit integer, ie. answer <= 2^31 - 1.
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def tribonacci(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n == 0:
            return 0
        if n == 1 or n == 2:
            return 1
        res = [0] * (n + 1)
        res[0] = 0
        res[1] = 1
        res[2] = 1
        for i in range(3, n+1):
            res[i] = res[i-1]+res[i-2]+res[i-3]
        return res[n]

        
```
