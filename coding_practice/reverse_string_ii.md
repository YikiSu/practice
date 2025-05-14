Location: https://leetcode.com/problems/reverse-string-ii/description/
# Question
Given a string s and an integer k, reverse the first k characters for every 2k characters counting from the start of the string.

If there are fewer than k characters left, reverse all of them. If there are less than 2k but greater than or equal to k characters, then reverse the first k characters and leave the other as original.

 
# Example

## Example 1:

Input: s = "abcdefg", k = 2

Output: "bacdfeg"

## Example 2:

Input: s = "abcd", k = 2

Output: "bacd"

## Constraints:

1 <= s.length <= 104\
s consists of only lowercase English letters.\
1 <= k <= 104
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def reverseStr(self, s, k):
        """
        :type s: str
        :type k: int
        :rtype: str
        """
        for ind in range(0, len(s), 2*k):
            if ind+k<len(s):
                # s[ind:ind+k] = s[ind:ind+k][::-1]
                s = s[:ind]+s[ind:ind+k][::-1]+s[ind+k:]
            else:
                # s[ind:] = s[ind:][::-1]
                s = s[:ind]+s[ind:][::-1]
        return s
```
