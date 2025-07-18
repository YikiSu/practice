Location: https://leetcode.com/problems/number-of-matching-subsequences/description/
# Question
Given a string s and an array of strings words, return the number of words[i] that is a subsequence of s.

A subsequence of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

For example, "ace" is a subsequence of "abcde".

 
# Example

## Example 1:

Input: s = "abcde", words = ["a","bb","acd","ace"]

Output: 3

Explanation: There are three strings in words that are a subsequence of s: "a", "acd", "ace".

## Example 2:

Input: s = "dsahjpjauf", words = ["ahjpjau","ja","ahbwzgqnuk","tnmlanowax"]

Output: 2

## Constraints:

1 <= s.length <= 5 * 104\
1 <= words.length <= 5000\
1 <= words[i].length <= 50\
s and words[i] consist of only lowercase English letters.
 

# My solution 
```python
import collections
class Solution(object):
    def numMatchingSubseq(self, s, words):
        """
        :type s: str
        :type words: List[str]
        :rtype: int
        """
        ans = 0
        cnt = collections.Counter(words)
        for word in cnt.keys():
            curr = word
            l = 0
            while l < len(s) and word != "":
                if word[0] == s[l]:
                    word = word[1:]
                l += 1
            if word == "":
                ans += cnt[curr]
        return ans
            
```
