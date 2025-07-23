Location: https://leetcode.com/problems/minimum-remove-to-make-valid-parentheses/description/
# Question
Given a string s of '(' , ')' and lowercase English characters.

Your task is to remove the minimum number of parentheses ( '(' or ')', in any positions ) so that the resulting parentheses string is valid and return any valid string.

Formally, a parentheses string is valid if and only if:

- It is the empty string, contains only lowercase characters, or
- It can be written as AB (A concatenated with B), where A and B are valid strings, or
- It can be written as (A), where A is a valid string.

 
# Example

## Example 1:

Input: s = "lee(t(c)o)de)"

Output: "lee(t(c)o)de"

Explanation: "lee(t(co)de)" , "lee(t(c)ode)" would also be accepted.

## Example 2:

Input: s = "a)b(c)d"

Output: "ab(c)d"

## Example 3:

Input: s = "))(("

Output: ""

Explanation: An empty string is also valid.
 

## Constraints:

1 <= s.length <= 105\
s[i] is either '(' , ')', or lowercase English letter.
 

# My solution 
```python
class Solution(object):
    def minRemoveToMakeValid(self, s):
        """
        :type s: str
        :rtype: str
        """
        curr = []
        ans = []
        cnt = 0
        for st in s:
            if st not in ["(",")"]:
                ans.append(st)
                cnt += 1
            elif st == "(":
                ans.append(st)
                cnt += 1
                curr.append(cnt)
            elif st == ")" and len(curr) != 0:
                ans.append(st)
                cnt += 1
                curr.pop(-1)
            else:
                continue
        if curr:
            # print(ans)
            for ind in curr[::-1]:
                # print(ind)
                ans.pop(ind-1)
        return "".join(ans)
```
