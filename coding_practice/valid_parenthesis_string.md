Location: https://leetcode.com/problems/valid-parenthesis-string/description/
# Question
Given a string s containing only three types of characters: '(', ')' and '*', return true if s is valid.

The following rules define a valid string:

- Any left parenthesis '(' must have a corresponding right parenthesis ')'.
- Any right parenthesis ')' must have a corresponding left parenthesis '('.
- Left parenthesis '(' must go before the corresponding right parenthesis ')'.
- '*' could be treated as a single right parenthesis ')' or a single left parenthesis '(' or an empty string "".
# Example

## Example 1:

Input: s = "()"

Output: true

## Example 2:

Input: s = "(*)"

Output: true

## Example 3:

Input: s = "(*))"

Output: true
 

## Constraints:

1 <= s.length <= 100\
s[i] is '(', ')' or '*'.
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def checkValidString(self, s):
        """
        :type s: str
        :rtype: bool
        """
        star = []
        dp = []
        for ind, st in enumerate(s):
            # print(st)
            if st == "(":
                dp.append(ind)
            elif st == "*":
                star.append(ind)
            else:
                if dp:
                    dp.pop(-1)
                elif star:
                    star.pop(-1)
                else:
                    return False
        while star and dp:
            if star[-1] < dp[-1]:
                return False
            star.pop(-1)
            dp.pop(-1)
        return len(dp) == 0
        
```
