Location: https://leetcode.com/problems/permutation-in-string/description/
# Question
Given two strings s1 and s2, return true if s2 contains a permutation of s1, or false otherwise.

In other words, return true if one of s1's permutations is the substring of s2.
# Example

## Example 1:

Input: s1 = "ab", s2 = "eidbaooo"

Output: true

Explanation: s2 contains one permutation of s1 ("ba").

## Example 2:

Input: s1 = "ab", s2 = "eidboaoo"

Output: false

## Constraints:

1 <= s1.length, s2.length <= 104\
s1 and s2 consist of lowercase English letters.
 

# My solution 
```python
class Solution(object):
    def checkInclusion(self, s1, s2):
        """
        :type s1: str
        :type s2: str
        :rtype: bool
        """
        n = len(s1)
        starting = 0
        while starting < len(s2)-n+1:
            if sorted(s1) == sorted(s2[starting:starting+n]):
                return True
            else:
                if s2[starting+n-1] not in s1:
                    starting += n
                else:
                    starting += 1
        return False
```
