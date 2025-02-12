Location: https://leetcode.com/problems/length-of-the-longest-alphabetical-continuous-substring/description/
# Question
An alphabetical continuous string is a string consisting of consecutive letters in the alphabet. In other words, it is any substring of the string "abcdefghijklmnopqrstuvwxyz".
- For example, "abc" is an alphabetical continuous string, while "acb" and "za" are not.
</br>Given a string s consisting of lowercase letters only, return the length of the longest alphabetical continuous substring.


# Example

## Example 1:

Input: s = "abacaba"

Output: 2

Explanation: There are 4 distinct continuous substrings: "a", "b", "c" and "ab".\
"ab" is the longest continuous substring.

## Example 2:

Input: s = "abcde"

Output: 5

Explanation: "abcde" is the longest continuous substring.

Constraints:

1 <= s.length <= 105\
s consists of only English lowercase letters.
 

# My solution 
```python
class Solution(object):
    def longestContinuousSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        ans = set()
        starting = 0
        moving = starting + 1
        curr = s[starting]
        while starting < len(s) and moving < len(s):
            if ord(curr[-1]) + 1 == ord(s[moving]):
                curr += s[moving]
                moving += 1
            else:
                ans.add(curr)
                starting = moving 
                moving += 1
                curr = s[starting]
        ans.add(curr)
        return len(max(ans, key=len))


        
```
