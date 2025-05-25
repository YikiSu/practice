Location: https://leetcode.com/problems/longest-palindrome-by-concatenating-two-letter-words/description/?envType=daily-question&envId=2025-05-25
# Question
You are given an array of strings words. Each element of words consists of two lowercase English letters.

Create the longest possible palindrome by selecting some elements from words and concatenating them in any order. Each element can be selected at most once.

Return the length of the longest palindrome that you can create. If it is impossible to create any palindrome, return 0.

A palindrome is a string that reads the same forward and backward.
 
# Example

## Example 1:

Input: words = ["lc","cl","gg"]

Output: 6

Explanation: One longest palindrome is "lc" + "gg" + "cl" = "lcggcl", of length 6.\
Note that "clgglc" is another longest palindrome that can be created.

## Example 2:

Input: words = ["ab","ty","yt","lc","cl","ab"]

Output: 8

Explanation: One longest palindrome is "ty" + "lc" + "cl" + "yt" = "tylcclyt", of length 8.\
Note that "lcyttycl" is another longest palindrome that can be created.

## Example 3:

Input: words = ["cc","ll","xx"]

Output: 2

Explanation: One longest palindrome is "cc", of length 2.\
Note that "ll" is another longest palindrome that can be created, and so is "xx".
 

## Constraints:

1 <= words.length <= 105\
words[i].length == 2\
words[i] consists of lowercase English letters.
 

# My solution
```python
import collections
class Solution(object):
    def longestPalindrome(self, words):
        """
        :type words: List[str]
        :rtype: int
        """
        cnt = collections.defaultdict(int)
        ans = 0
        for word in words:
            cnt[word] += 1
            if word == word[::-1]:
                if cnt[word] == 2:
                    ans += 2
                    cnt[word] = 0
            elif word[::-1] in cnt.keys():
                curr = min(cnt[word], cnt[word[::-1]])
                ans += curr*2
                cnt[word] = max(cnt[word]-curr, 0)
                cnt[word[::-1]] = max(cnt[word[::-1]]-curr, 0)
        for key, val in cnt.items():
            if key == key[::-1] and val > 0:
                ans += 1
                break
        return ans*2
         
```
