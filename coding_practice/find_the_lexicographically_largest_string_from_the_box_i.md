Location: https://leetcode.com/problems/find-the-lexicographically-largest-string-from-the-box-i/description/?envType=daily-question&envId=2025-09-09
# Question
You are given a string word, and an integer numFriends.

Alice is organizing a game for her numFriends friends. There are multiple rounds in the game, where in each round:

word is split into numFriends non-empty strings, such that no previous round has had the exact same split.
All the split words are put into a box.
Find the lexicographically largest string from the box after all the rounds are finished.
 
# Example

## Example 1:

Input: word = "dbca", numFriends = 2

Output: "dbc"

Explanation: 

All possible splits are:

"d" and "bca".\
"db" and "ca".\
"dbc" and "a".

## Example 2:

Input: word = "gggg", numFriends = 4

Output: "g"

Explanation: 

The only possible split is: "g", "g", "g", and "g".

## Constraints:

1 <= word.length <= 5 * 103\
word consists only of lowercase English letters.\
1 <= numFriends <= word.length
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def answerString(self, word, numFriends):
        """
        :type word: str
        :type numFriends: int
        :rtype: str
        """
        if numFriends == 1:
            return word
        ans = ""
        max_len = len(word)-numFriends+1
        for i in range(len(word)):
            cur = word[i:i+max_len]
            ans = max(cur, ans)
        return ans
```
