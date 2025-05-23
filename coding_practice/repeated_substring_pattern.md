Location: https://leetcode.com/problems/repeated-substring-pattern/description/
# Question
Given a string s, check if it can be constructed by taking a substring of it and appending multiple copies of the substring together.
# Example

## Example 1:

Input: s = "abab"

Output: true

Explanation: It is the substring "ab" twice.

## Example 2:

Input: s = "aba"

Output: false

## Example 3:

Input: s = "abcabcabcabc"

Output: true

Explanation: It is the substring "abc" four times or the substring "abcabc" twice.
 

## Constraints:

1 <= s.length <= 104\
s consists of lowercase English letters.

# My solution 
```python
class Solution(object):
    def repeatedSubstringPattern(self, s):
        """
        :type s: str
        :rtype: bool
        """
        curr = ""
        starting = 0
        while starting < len(s):
            if curr and s[starting] == curr[0]:
                length = len(curr)
                if len(s)%length == 0:
                    check_=True
                    for ind in range(0, len(s), length):
                        if s[ind:ind+length] != curr:
                            curr += s[starting]
                            starting += 1
                            check_ = False
                            break
                    if check_:
                        return True
                else:
                    curr += s[starting]
                    starting += 1
            else:
                curr += s[starting]
                starting += 1
        return False
```
