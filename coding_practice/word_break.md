Location: https://leetcode.com/problems/word-break/description/
# Question
Given a string s and a dictionary of strings wordDict, return true if s can be segmented into a space-separated sequence of one or more dictionary words.

Note that the same word in the dictionary may be reused multiple times in the segmentation.

# Example

## Example 1:

Input: s = "leetcode", wordDict = ["leet","code"]

Output: true

Explanation: Return true because "leetcode" can be segmented as "leet code".

## Example 2:

Input: s = "applepenapple", wordDict = ["apple","pen"]

Output: true

Explanation: Return true because "applepenapple" can be segmented as "apple pen apple".\
Note that you are allowed to reuse a dictionary word.

## Example 3:

Input: s = "catsandog", wordDict = ["cats","dog","sand","and","cat"]

Output: false

## Constraints:

1 <= s.length <= 300\
1 <= wordDict.length <= 1000\
1 <= wordDict[i].length <= 20\
s and wordDict[i] consist of only lowercase English letters.\
All the strings of wordDict are unique.
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def wordBreak(self, s, wordDict):
        """
        :type s: str
        :type wordDict: List[str]
        :rtype: bool
        """
        # curr = s
        # for word in wordDict:
        #     # print(word)
        #     # print(curr)
        #     # print(curr.split(word))
        #     curr = "".join(curr.split(word))
        # return curr == ""
        df = [False] * (len(s)+1)
        df[0] = True
        for i in range(1, len(s)+1):
            for j in range(i):
                if df[j] and s[j:i] in wordDict:
                    df[i] = True
        # print(df)
        return df[len(s)]
        
```
