Location: https://leetcode.com/problems/longest-valid-parentheses/description/
# Question
Given a string containing just the characters '(' and ')', return the length of the longest valid (well-formed) parentheses substring.

 
# Example

## Example 1:

Input: s = "(()"

Output: 2

Explanation: The longest valid parentheses substring is "()".

## Example 2:

Input: s = ")()())"

Output: 4

Explanation: The longest valid parentheses substring is "()()".

## Example 3:

Input: s = ""

Output: 0

## Constraints:

0 <= s.length <= 3 * 104\
s[i] is '(', or ')'.

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def longestValidParentheses(self, s):
        """
        :type s: str
        :rtype: int
        """
        ans = -float('inf')
        dp = [-1]
        for ind, st in enumerate(s):
            if st == "(":
                dp.append(ind)
            else:
                dp.pop(-1)
                if dp:                    
                    ans = max(ans, ind-dp[-1])
                else:
                    dp.append(ind)
        return max(ans, 0)

```
