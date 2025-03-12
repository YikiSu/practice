Location: https://leetcode.com/problems/maximum-nesting-depth-of-the-parentheses/description/
# Question
Given a valid parentheses string s, return the nesting depth of s. The nesting depth is the maximum number of nested parentheses. 
# Example

## Example 1:

Input: s = "(1+(2*3)+((8)/4))+1"

Output: 3

Explanation:

Digit 8 is inside of 3 nested parentheses in the string.

## Example 2:

Input: s = "(1)+((2))+(((3)))"

Output: 3

Explanation:

Digit 3 is inside of 3 nested parentheses in the string.
## Example 3:

Input: s = "()(())((()()))"

Output: 3
 

## Constraints:

1 <= s.length <= 100\
s consists of digits 0-9 and characters '+', '-', '*', '/', '(', and ')'.\
It is guaranteed that parentheses expression s is a VPS.
 

# My solution 
```python
class Solution(object):
    def maxDepth(self, s):
        """
        :type s: str
        :rtype: int
        """
        stack = []
        ans = 0
        for st in s:
            if st in ["(",")"]:
                if st == ")" and stack[-1] == "(":
                    ans = max(ans, len(stack))
                    stack.pop(-1)
                else:
                    stack.append(st)
        return ans
                
        
```
