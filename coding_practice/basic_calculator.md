Location: https://leetcode.com/problems/basic-calculator/description/?envType=problem-list-v2&envId=stack
# Question
Given a string s representing a valid expression, implement a basic calculator to evaluate it, and return the result of the evaluation.

Note: You are not allowed to use any built-in function which evaluates strings as mathematical expressions, such as eval().
 
# Example

## Example 1:

Input: s = "1 + 1"

Output: 2

## Example 2:

Input: s = " 2-1 + 2 "

Output: 3

## Example 3:

Input: s = "(1+(4+5+2)-3)+(6+8)"

Output: 23
 

Constraints:

1 <= s.length <= 3 * 105\
s consists of digits, '+', '-', '(', ')', and ' '.\
s represents a valid expression.\
'+' is not used as a unary operation (i.e., "+1" and "+(2 + 3)" is invalid).\
'-' could be used as a unary operation (i.e., "-1" and "-(2 + 3)" is valid).\
There will be no two consecutive operators in the input.\
Every number and running calculation will fit in a signed 32-bit integer.
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def calculate(self, s):
        """
        :type s: str
        :rtype: int
        """
        ans = []
        sign = 1
        num = 0
        res = 0
        s = s.replace(" ","")
        for ind, ch in enumerate(s):
            if ch.isdigit():
                num = num*10 + int(ch)
            if ch in "+-" or ch == "(" or ch==")" or ind == len(s)-1:
                if ch in "+-" or ind == len(s)-1:
                    res += sign * num
                    num = 0
                if ch == "+":
                    sign = 1
                elif ch == "-":
                    sign = -1
                elif ch == "(":
                    ans.append(res)
                    ans.append(sign)
                    res = 0
                    sign = 1
                elif ch == ")":
                    res += sign*num
                    num = 0
                    res *= ans.pop()
                    res += ans.pop()
        return res
        
```
