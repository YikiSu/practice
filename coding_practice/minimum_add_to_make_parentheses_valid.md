Location: https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/description/
# Question
A parentheses string is valid if and only if:

- It is the empty string,
- It can be written as AB (A concatenated with B), where A and B are valid strings, or
- It can be written as (A), where A is a valid string.
</br>You are given a parentheses string s. In one move, you can insert a parenthesis at any position of the string.

- For example, if s = "()))", you can insert an opening parenthesis to be "(()))" or a closing parenthesis to be "())))".
</br>Return the minimum number of moves required to make s valid.

 
# Example

## Example 1:

Input: s = "())"

Output: 1

## Example 2:

Input: s = "((("

Output: 3

Constraints:

1 <= s.length <= 1000\
s[i] is either '(' or ')'.
 

# My solution 
```python
class Solution(object):
    def minAddToMakeValid(self, s):
        """
        :type s: str
        :rtype: int
        """
        ans = []
        for st in s:
            if st == "(":
                ans.append(st)
            elif st == ")" and ans and ans[-1] == "(":
                ans.pop()
            else:
                ans.append(st)
        return len(ans)
        
        
```
