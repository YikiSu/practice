Location: https://leetcode.com/problems/happy-number/description/
# Question
Write an algorithm to determine if a number n is happy.

A happy number is a number defined by the following process:

- Starting with any positive integer, replace the number by the sum of the squares of its digits.
- Repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1.
- Those numbers for which this process ends in 1 are happy.

Return true if n is a happy number, and false if not.
# Example

## Example 1:

Input: n = 19

Output: true

Explanation:\
12 + 92 = 82\
82 + 22 = 68\
62 + 82 = 100\
12 + 02 + 02 = 1
## Example 2:

Input: n = 2

Output: false

Constraints:

1 <= n <= 231 - 1
 

# My solution (follow hints on ChatGPT)
```python
class Solution(object):
    def isHappy(self, n):
        """
        :type n: int
        :rtype: bool
        """
        if n == 1:
            return True
        seen = set()
        while True:
            curr = 0
            l = len(str(n))-1
            for i in range(l, -1, -1):
                new = n//(10)**i
                curr += (new)**2
                n -= new*((10)**i)
            if curr in seen:
                return False
            else:
                if curr == 1:
                    return True
                n = curr
                seen.add(curr)
        return n == 1
        
```
