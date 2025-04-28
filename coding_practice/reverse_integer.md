Location: https://leetcode.com/problems/reverse-integer/description/
# Question
Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).

 
# Example

## Example 1:

Input: x = 123

Output: 321

## Example 2:

Input: x = -123

Output: -321

## Example 3:

Input: x = 120

Output: 21
 
## Constraints:

-231 <= x <= 231 - 1
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        # if x < 0:
        #     return -int(str(-x)[::-1])
        # else:
        #     return int(str(x)[::-1])
        ans = 0
        sign = 1
        if x < 0:
            sign = -1
            x = -x
        while x > 0:
            curr = x%10
            if ans <= 2147483648/10:
                ans = ans*10+curr
                x = x//10
            else:
                return 0
        return sign*ans
```
