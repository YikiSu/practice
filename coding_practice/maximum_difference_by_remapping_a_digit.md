Location: https://leetcode.com/problems/maximum-difference-by-remapping-a-digit/description/
# Question
You are given an integer num. You know that Bob will sneakily remap one of the 10 possible digits (0 to 9) to another digit.

Return the difference between the maximum and minimum values Bob can make by remapping exactly one digit in num.

Notes:

- When Bob remaps a digit d1 to another digit d2, Bob replaces all occurrences of d1 in num with d2.
- Bob can remap a digit to itself, in which case num does not change.
- Bob can remap different digits for obtaining minimum and maximum values respectively.
- The resulting number after remapping can contain leading zeroes.
 
# Example

## Example 1:

Input: num = 11891

Output: 99009

Explanation: \
To achieve the maximum value, Bob can remap the digit 1 to the digit 9 to yield 99899.\
To achieve the minimum value, Bob can remap the digit 1 to the digit 0, yielding 890.\
The difference between these two numbers is 99009.

## Example 2:

Input: num = 90

Output: 99

Explanation:\
The maximum value that can be returned by the function is 99 (if 0 is replaced by 9) and the minimum value that can be returned by the function is 0 (if 9 is replaced by 0).\
Thus, we return 99.

## Constraints:

1 <= num <= 108
 

# My solution 
```python
class Solution(object):
    def minMaxDifference(self, num):
        """
        :type num: int
        :rtype: int
        """
        digits = [st for st in str(num)]
        if len(digits) == 1:
            return 9
        max_ = "0"
        min_ = "9"
        for digit in digits:
            if digit != "9":
                max_ = digit
                break
        for digit in digits:
            if digit != "0":
                min_ = digit
                break

        diff = int("".join(["9" if st==max_ else st for st in digits])) - int("".join(["0" if st==min_ else st for st in digits]))
        # print(int("".join(["9" if st==max_ else st for st in digits])))
        # print(int("".join(["0" if st==min_ else st for st in digits])))
        return diff
        
```
