Location: https://leetcode.com/problems/minimum-additions-to-make-valid-string/description/?envType=problem-list-v2&envId=stack
# Question
Given a string word to which you can insert letters "a", "b" or "c" anywhere and any number of times, return the minimum number of letters that must be inserted so that word becomes valid.

A string is called valid if it can be formed by concatenating the string "abc" several times.
 
# Example

## Example 1:

Input: word = "b"

Output: 2

Explanation: Insert the letter "a" right before "b", and the letter "c" right next to "b" to obtain the valid string "abc".

## Example 2:

Input: word = "aaa"

Output: 6

Explanation: Insert letters "b" and "c" next to each "a" to obtain the valid string "abcabcabc".

## Example 3:

Input: word = "abc"

Output: 0

Explanation: word is already valid. No modifications are needed. 
 

Constraints:

1 <= word.length <= 50\
word consists of letters "a", "b" and "c" only. 
 

# My solution 
```python
class Solution(object):
    def addMinimum(self, word):
        """
        :type word: str
        :rtype: int
        """
        checked = "abc"
        cp = 0
        wp = 0
        ans = 0
        while wp < len(word):
            if word[wp] == checked[cp]:
                wp += 1
                cp += 1
                if cp > len(checked)-1 and wp < len(word):
                    cp = 0
            elif word[wp] != checked[cp]:
                ans += 1
                cp += 1
                if cp > len(checked)-1 and wp < len(word):
                    cp = 0
        if cp < len(checked):
            ans += len(checked)-cp
        return ans
        
```
