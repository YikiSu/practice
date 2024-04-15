Location: https://leetcode.com/problems/valid-anagram/
# Question
An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

# Example
## Example 1:

Input: s = "anagram", t = "nagaram"

Output: true

## Example 2:

Input: s = "rat", t = "car"

Output: false

# My solution
```python
class Solution(object):
    def isAnagram(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        return sorted(list(s)) == sorted(list(t))
```

# Fastest solution
```python
class Solution(object):
    def isAnagram(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        if len(s) != len(t):
            return False
        for char in set(s):
            if s.count(char) != t.count(char):
                return  False
        return True
```
