Location: https://leetcode.com/problems/break-a-palindrome/description/
# Question
Given a palindromic string of lowercase English letters palindrome, replace exactly one character with any lowercase English letter so that the resulting string is not a palindrome and that it is the lexicographically smallest one possible.

Return the resulting string. If there is no way to replace a character to make it not a palindrome, return an empty string.

A string a is lexicographically smaller than a string b (of the same length) if in the first position where a and b differ, a has a character strictly smaller than the corresponding character in b. For example, "abcc" is lexicographically smaller than "abcd" because the first position they differ is at the fourth character, and 'c' is smaller than 'd'.

 
# Example

## Example 1:

Input: palindrome = "abccba"

Output: "aaccba"

Explanation: There are many ways to make "abccba" not a palindrome, such as "zbccba", "aaccba", and "abacba".\
Of all the ways, "aaccba" is the lexicographically smallest.

## Example 2:

Input: palindrome = "a"

Output: ""

Explanation: There is no way to replace a single character to make "a" not a palindrome, so return an empty string.

## Constraints:

1 <= palindrome.length <= 1000\
palindrome consists of only lowercase English letters.
 

# My solution (follows hints)
```python
class Solution(object):
    def breakPalindrome(self, palindrome):
        """
        :type palindrome: str
        :rtype: str
        """
        ans = ""
        if len(palindrome) == 1:
            return ""
        if len(palindrome) == 2:
            if palindrome[-1] == "a":
                return "ab"
            else:
                ans = ans[0]+"a"
                return ans
        for ind, st in enumerate(palindrome):
            if st != "a":
                if set(palindrome[:ind]) != set(palindrome[ind+1:]) != "a":
                    ans = palindrome[:ind]+"a"+palindrome[ind+1:]
                    return ans
                else:
                    ans = palindrome[:-1]+"b"
                    return ans
```
