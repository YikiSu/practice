Location: https://leetcode.com/problems/check-if-word-is-valid-after-substitutions/description/
# Question
Given a string s, determine if it is valid.

A string s is valid if, starting with an empty string t = "", you can transform t into s after performing the following operation any number of times:

- Insert string "abc" into any position in t. More formally, t becomes tleft + "abc" + tright, where t == tleft + tright. Note that tleft and tright may be empty.

Return true if s is a valid string, otherwise, return false.
 
# Example

## Example 1:

Input: s = "aabcbc"

Output: true

Explanation:\
"" -> "abc" -> "aabcbc"\
Thus, "aabcbc" is valid.

## Example 2:

Input: s = "abcabcababcc"

Output: true

Explanation:\
"" -> "abc" -> "abcabc" -> "abcabcabc" -> "abcabcababcc"\
Thus, "abcabcababcc" is valid.

## Example 3:

Input: s = "abccba"

Output: false

Explanation: It is impossible to get "abccba" using the operation.
 

## Constraints:

1 <= s.length <= 2 * 104\
s consists of letters 'a', 'b', and 'c'
 

# My solution 
```python
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        left = ""
        curr = ""
        for st in s:
            # if left == "abc":
            #     left = ""
            # if curr == "abc":
            #     curr = ""
            if st == "a":
                if curr == "":
                    curr += st
                else:
                    left += curr
                    curr = st
            if st == "b":
                if curr == "a":
                    curr += st
                else:
                    if len(left)>=1 and left[-1] == "a":
                        curr = "ab"
                        left = left[:-1]
                    else:
                        return False
            if st == "c":
                if curr == "ab":
                    curr =""
                else:
                    if len(left)>=2 and left[-2:] == "ab":
                        curr = ""
                        left = left[:-2]
                    else:
                        return False
        return (left == "abc" or left == "") and (curr == "" or curr == "abc")
```
