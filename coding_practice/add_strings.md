Location: https://leetcode.com/problems/add-strings/description/
# Question
Given two non-negative integers, num1 and num2 represented as string, return the sum of num1 and num2 as a string.

You must solve the problem without using any built-in library for handling large integers (such as BigInteger). You must also not convert the inputs to integers directly.

 
# Example

## Example 1:

Input: num1 = "11", num2 = "123"

Output: "134"

## Example 2:

Input: num1 = "456", num2 = "77"

Output: "533"

## Example 3:

Input: num1 = "0", num2 = "0"

Output: "0"

## Constraints:

1 <= num1.length, num2.length <= 104\
num1 and num2 consist of only digits.\
num1 and num2 don't have any leading zeros except for the zero itself.
 

# My solution 
```python
class Solution(object):
    def addStrings(self, num1, num2):
        """
        :type num1: str
        :type num2: str
        :rtype: str
        """
        num1 = [st for st in num1]
        num2 = [st for st in num2]
        pre = 0
        ans = ""
        r = -1
        while num1 and num2:
            curr = int(num1.pop(-1))+int(num2.pop(-1)) + pre
            if curr < 10:
                pre = 0
                ans = str(curr)+ans
            else:
                pre = curr//10
                ans = str(curr-pre*10)+ans
        while num1:
            curr = int(num1.pop(-1)) + pre
            if curr < 10:
                pre = 0
                ans = str(curr)+ans
            else:
                pre = curr//10
                ans = str(curr-pre*10)+ans
        while num2:
            curr = int(num2.pop(-1)) + pre
            if curr < 10:
                pre = 0
                ans = str(curr)+ans
            else:
                pre = curr//10
                ans = str(curr-pre*10)+ans
        if pre != 0:
            ans = str(pre)+ans
        if ans == "":
            return "0"
        else:
            return ans

                
```
