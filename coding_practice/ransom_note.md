Location: https://leetcode.com/problems/ransom-note/

# Questions
Given two strings ransomNote and magazine, return true if ransomNote can be constructed by using the letters from magazine and false otherwise.

Each letter in magazine can only be used once in ransomNote.

# Example 
## Example 1:

Input: ransomNote = "a", magazine = "b"

Output: false

## Example 2:

Input: ransomNote = "aa", magazine = "ab"

Output: false

## Example 3:

Input: ransomNote = "aa", magazine = "aab"

Output: true

# My solution
```python
class Solution(object):
    def canConstruct(self, ransomNote, magazine):
        """
        :type ransomNote: str
        :type magazine: str
        :rtype: bool
        """
        r_count = Counter(ransomNote)
        m_count = Counter(magazine)
        for l in ransomNote:
            if m_count[l] < r_count[l]:
                return False
        return True
```

# Fastest solution
```python
class Solution(object):
    def canConstruct(self, ransomNote, magazine):
        """
        :type ransomNote: str
        :type magazine: str
        :rtype: bool
        """
        if len(ransomNote) > len(magazine):
            return False
        count = 0
        ransomNote_length = set()
        for c in ransomNote:
            if c not in ransomNote_length:
                ransomNote_length.add(c)
                if ransomNote.count(c) > magazine.count(c):
                    #print(ransomNote.count(c),magazine.count(c),ransomNote_length)
                    return False
        return True


```
