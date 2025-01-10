Location: https://leetcode.com/problems/is-subsequence/description/?envType=study-plan-v2&envId=leetcode-75
# Question
Given two strings s and t, return true if s is a subsequence of t, or false otherwise.

A subsequence of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., "ace" is a subsequence of "abcde" while "aec" is not).

# Example

## Example 1:

Input: s = "abc", t = "ahbgdc"

Output: true

## Example 2:

Input: s = "axc", t = "ahbgdc"

Output: false

Constraints:
- 0 <= s.length <= 100
- 0 <= t.length <= 104
- s and t consist only of lowercase English letters.
 

# My solution 
```python
class Solution(object):
    def isSubsequence(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        if s == "":
            return True
        if t == "":
            return False
        if s == "" and t == "":
            return True
        s1 = [st for st in s]
        for st in t:
            if st == s1[0]:
                s1.pop(0)
                if len(s1) == 0:
                    return True
        return len(s1)==0
```
