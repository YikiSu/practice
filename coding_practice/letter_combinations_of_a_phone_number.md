Location: https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/
# Question
Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

 
# Example

## Example 1:
Input: digits = "23"

Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]

## Example 2:
Input: digits = ""

Output: []

## Example 3:
Input: digits = "2"

Output: ["a","b","c"]

Constraints:

- 0 <= digits.length <= 4
- digits[i] is a digit in the range ['2', '9'].
 

# My solution 
```python
import itertools
class Solution(object):
    def letterCombinations(self, digits):
        """
        :type digits: str
        :rtype: List[str]
        """
        if digits == "":
            return []
        num_str = {
            '1':'',
            '2':'abc',
            '3':'def',
            '4':'ghi',
            '5':'jkl',
            '6':'mno',
            '7':'pqrs',
            '8':'tuv',
            '9':'wxyz'
        }
        digit_list = [list(num_str[num]) for num in digits]
        return ["".join(s) for s in itertools.product(*digit_list)]

```
