Location: https://leetcode.com/problems/keyboard-row/description/?envType=problem-list-v2&envId=hash-table
# Question
Given an array of strings words, return the words that can be typed using letters of the alphabet on only one row of American keyboard like the image below.

Note that the strings are case-insensitive, both lowercased and uppercased of the same letter are treated as if they are at the same row.

In the American keyboard:

the first row consists of the characters "qwertyuiop",
the second row consists of the characters "asdfghjkl", and
the third row consists of the characters "zxcvbnm".
 
# Example

## Example 1:

Input: words = ["Hello","Alaska","Dad","Peace"]

Output: ["Alaska","Dad"]

Explanation:

Both "a" and "A" are in the 2nd row of the American keyboard due to case insensitivity.

## Example 2:

Input: words = ["omk"]

Output: []

## Example 3:

Input: words = ["adsdf","sfd"]

Output: ["adsdf","sfd"]
 

## Constraints:

1 <= words.length <= 20\
1 <= words[i].length <= 100\
words[i] consists of English letters (both lowercase and uppercase). 

# My solution
```python
class Solution(object):
    def findWords(self, words):
        """
        :type words: List[str]
        :rtype: List[str]
        """
        fir = {}
        ans = []
        for st in  "qwertyuiop":
            fir[st] = 1
        for st in "asdfghjkl":
            fir[st] = 2
        for st in "zxcvbnm":
            fir[st] = 3
        for word in words:
            same = True
            starting = fir[word[0].lower()]
            for i in range(1, len(word)):
                if fir[word[i].lower()] != starting:
                    same = False
                    break
            if same:
                ans.append(word)
        return ans     
```
