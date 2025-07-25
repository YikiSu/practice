Location: https://leetcode.com/problems/multiply-strings/description/
# Question
Given two non-negative integers num1 and num2 represented as strings, return the product of num1 and num2, also represented as a string.

Note: You must not use any built-in BigInteger library or convert the inputs to integer directly.

 
# Example

## Example 1:

Input: num1 = "2", num2 = "3"

Output: "6"

## Example 2:

Input: num1 = "123", num2 = "456"

Output: "56088"

## Constraints:

1 <= num1.length, num2.length <= 200\
num1 and num2 consist of digits only.\
Both num1 and num2 do not contain any leading zero, except the number 0 itself.
 

# My solution
```python
class Solution(object):
    def multiply(self, num1, num2):
        """
        :type num1: str
        :type num2: str
        :rtype: str
        """
        if len(num1) < len(num2):
            num1, num2 = num2, num1
        else:
            num1, num2 = num1, num2
        ans = 0
        cnt = 0
        for st1 in num1[::-1]:
            curr = 0
            for ind, st2 in enumerate(num2[::-1]):
                curr += int(st1)*int(st2)*(10**ind)
            ans += curr*(10**cnt)
            cnt += 1
        return str(ans)

```
