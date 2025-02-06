Location: https://leetcode.com/problems/fibonacci-number/description/?envType=problem-list-v2&envId=dynamic-programming
# Question
The Fibonacci numbers, commonly denoted F(n) form a sequence, called the Fibonacci sequence, such that each number is the sum of the two preceding ones, starting from 0 and 1. That is,
</br>F(0) = 0, F(1) = 1
</br>F(n) = F(n - 1) + F(n - 2), for n > 1.
</br>Given n, calculate F(n).

# Example

## Example 1:

Input: n = 2

Output: 1

Explanation: F(2) = F(1) + F(0) = 1 + 0 = 1.

## Example 2:

Input: n = 3

Output: 2

Explanation: F(3) = F(2) + F(1) = 1 + 1 = 2.

## Example 3:

Input: n = 4

Output: 3

Explanation: F(4) = F(3) + F(2) = 2 + 1 = 3.

Constraints:
- 0 <= n <= 30

# My solution
```python
class Solution(object):
    def fib(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n == 0:
            return 0
        if n == 1:
            return 1
        ans = [0]*n
        ans[1] = 1
        for i in range(2, n):
            ans[i] = ans[i-1]+ans[i-2]
        return ans[-1]+ans[-2]
        

```
