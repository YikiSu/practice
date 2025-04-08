Location: https://leetcode.com/problems/append-characters-to-string-to-make-subsequence/description/?envType=problem-list-v2&envId=two-pointers&
# Question
You are given two strings s and t consisting of only lowercase English letters.

Return the minimum number of characters that need to be appended to the end of s so that t becomes a subsequence of s.

A subsequence is a string that can be derived from another string by deleting some or no characters without changing the order of the remaining characters.

 
# Example

## Example 1:

Input: s = "coaching", t = "coding"

Output: 4

Explanation: Append the characters "ding" to the end of s so that s = "coachingding".\
Now, t is a subsequence of s ("coachingding").\
It can be shown that appending any 3 characters to the end of s will never make t a subsequence.

## Example 2:

Input: s = "abcde", t = "a"

Output: 0

Explanation: t is already a subsequence of s ("abcde").

## Example 3:

Input: s = "z", t = "abcde"

Output: 5

Explanation: Append the characters "abcde" to the end of s so that s = "zabcde".\
Now, t is a subsequence of s ("zabcde").\
It can be shown that appending any 4 characters to the end of s will never make t a subsequence.
 

## Constraints:

1 <= s.length, t.length <= 105\
s and t consist only of lowercase English letters.
 

# My solution 
```python
class Solution(object):
    def appendCharacters(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: int
        """
        l1, l2 = 0, 0
        while l1 < len(s) and l2 < len(t):
            if s[l1] == t[l2]:
                l1 += 1
                l2 += 1
            else:
                l1 += 1
        if l2 == len(t):
            return 0
        else:
            return len(t)-l2
```
