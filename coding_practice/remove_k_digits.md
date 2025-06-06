Location: https://leetcode.com/problems/remove-k-digits/description/?envType=problem-list-v2&envId=monotonic-stack
# Question
Given string num representing a non-negative integer num, and an integer k, return the smallest possible integer after removing k digits from num.
 
# Example

## Example 1:

Input: num = "1432219", k = 3

Output: "1219"

Explanation: Remove the three digits 4, 3, and 2 to form the new number 1219 which is the smallest.

## Example 2:

Input: num = "10200", k = 1

Output: "200"

Explanation: Remove the leading 1 and the number is 200. Note that the output must not contain leading zeroes.

## Example 3:

Input: num = "10", k = 2

Output: "0"

Explanation: Remove all the digits from the number and it is left with nothing which is 0.
 

## Constraints:

1 <= k <= num.length <= 105\
num consists of only digits.\
num does not have any leading zeros except for the zero itself.
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def removeKdigits(self, num, k):
        """
        :type num: str
        :type k: int
        :rtype: str
        """
        if k == len(num):
            return "0"
        stack = []
        for st in num:
            while stack and st < stack[-1] and k > 0:
                stack.pop()
                k -= 1
            stack.append(st)
        while k:
            stack.pop()
            k -= 1
        if not stack:
            return "0"
        else:
            return str(int("".join(stack)))
```
