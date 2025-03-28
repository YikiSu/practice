Location: https://leetcode.com/problems/find-first-palindromic-string-in-the-array/description/
# Question
Given an array of strings words, return the first palindromic string in the array. If there is no such string, return an empty string "".

A string is palindromic if it reads the same forward and backward.
# Example

## Example 1:

Input: words = ["abc","car","ada","racecar","cool"]

Output: "ada"

Explanation: The first string that is palindromic is "ada".\
Note that "racecar" is also palindromic, but it is not the first.

## Example 2:

Input: words = ["notapalindrome","racecar"]

Output: "racecar"

Explanation: The first and only string that is palindromic is "racecar".

## Example 3:

Input: words = ["def","ghi"]

Output: ""

Explanation: There are no palindromic strings, so the empty string is returned.
 

## Constraints:

1 <= words.length <= 100\
1 <= words[i].length <= 100\
words[i] consists only of lowercase English letters.
 

# My solution 
```python
class Solution(object):
    def firstPalindrome(self, words):
        """
        :type words: List[str]
        :rtype: str
        """
        for word in words:
            if word[0] == word[-1]:
                n = len(word)
                if n%2 == 0:
                    if word[:(n//2)] == word[(n//2):][::-1]:
                        return word
                else:
                    if word[:(n//2)] == word[(n//2)+1:][::-1]:
                        return word
        return ""
        
```
