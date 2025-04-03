Location: https://leetcode.com/problems/valid-palindrome-ii/description/?envType=problem-list-v2&envId=two-pointers
# Question
Given a string s, return true if the s can be palindrome after deleting at most one character from it.

 
# Example

## Example 1:

Input: s = "aba"

Output: true

## Example 2:

Input: s = "abca"

Output: true

Explanation: You could delete the character 'c'.

## Example 3:

Input: s = "abc"

Output: false
 

## Constraints:

1 <= s.length <= 105\
s consists of lowercase English letters.
 

# My solution (follows instructions on solutions)
```python
import collections
class Solution(object):
    def validPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        def isPalindrome(st):
            l, r = 0, len(st)-1
            while l<=r:
                if st[l] != st[r]:
                    return False
                l += 1
                r -= 1
            return True
        left, right = 0, len(s)-1
        while left <= right:
            if s[left] != s[right]:
                check_left = isPalindrome(s[left:right])
                check_right = isPalindrome(s[left+1:right+1])
                return check_left or check_right
            left += 1
            right -= 1
        return True
```
