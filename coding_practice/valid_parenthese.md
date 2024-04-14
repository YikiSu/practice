Location: https://leetcode.com/problems/valid-parentheses/submissions/1232429311/

# Question
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.

# Example
## Example 1:

Input: s = "()"
  
Output: true

## Example 2:

Input: s = "()[]{}"

Output: true

## Example 3:

Input: s = "(]"
  
Output: false

# My answer
```python
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        string_match = {"(":")", "{":"}", "[":"]", ")":"", "}":"", "]":""}
        res_dict = []
        for item in s:
            if len(res_dict)==0:
                res_dict.append(item)
            elif item == string_match[res_dict[-1]]:
                res_dict.pop()
            else:
                res_dict.append(item)
        return len(res_dict) == 0
```

# Solution code
```python
class Solution(object):
    def isValid(self, s):
        stack = []
        dic = {")": "(", "]": "[", "}": "{"}
        for char in s:
            if char in ("(", "[", "{"):
                stack.append(char)
            elif char in (")", "]", "}"):
                if not stack or dic[char] != stack.pop():
                    return False
        return not stack
```
