Location: https://leetcode.com/problems/alternating-digit-sum/description/
# Question
You are given a positive integer n. Each digit of n has a sign according to the following rules:

- The most significant digit is assigned a positive sign.
- Each other digit has an opposite sign to its adjacent digits.

Return the sum of all digits with their corresponding sign.

# Example

## Example 1:

Input: n = 521

Output: 4

Explanation: (+5) + (-2) + (+1) = 4.
## Example 2:

Input: n = 111

Output: 1

Explanation: (+1) + (-1) + (+1) = 1.

## Example 3:

Input: n = 886996

Output: 0

Explanation: (+8) + (-8) + (+6) + (-9) + (+9) + (-6) = 0.
 

Constraints:

1 <= n <= 109
 

# My solution 
```python
class Solution(object):
    def alternateDigitSum(self, n):
        """
        :type n: int
        :rtype: int
        """
        pre = 1
        ans = ""
        for s in str(n):
            if pre == 1:
                ans += "+" + s
            else:
                ans += "-" + s
            pre *= -1
        return eval(ans)

        
```
