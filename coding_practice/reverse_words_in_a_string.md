Location: https://leetcode.com/problems/reverse-words-in-a-string/description/?envType=study-plan-v2&envId=leetcode-75
# Question
Given an input string s, reverse the order of the words.

A word is defined as a sequence of non-space characters. The words in s will be separated by at least one space.

Return a string of the words in reverse order concatenated by a single space.

Note that s may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.

# Example

## Example 1:

Input: s = "the sky is blue"\
Output: "blue is sky the"
## Example 2:

Input: s = "  hello world  "\
Output: "world hello"\
Explanation: Your reversed string should not contain leading or trailing spaces.
## Example 3:

Input: s = "a good   example"\
Output: "example good a"\
Explanation: You need to reduce multiple spaces between two words to a single space in the reversed string.

# My solution (borrowed hints from the previous exercise)
```python
class Solution(object):
    def reverseWords(self, s):
        """
        :type s: str
        :rtype: str
        """
        slist = s.split()
        starting = 0
        ending = len(slist)-1
        while starting < ending:
            slist[starting], slist[ending] = slist[ending], slist[starting]
            starting += 1
            ending -= 1
        return " ".join(slist)
```
# Fastest solution
```python
class Solution:
# @param s, a string
# @return a string
def reverseWords(self, s):
    return " ".join(s.strip().split()[::-1])
```
