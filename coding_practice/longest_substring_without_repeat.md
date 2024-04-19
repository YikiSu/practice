Location: https://leetcode.com/problems/longest-substring-without-repeating-characters/

# Question
Given a string s, find the length of the longest substring without repeating characters.

# Example
## Example 1:

Input: s = "abcabcbb"

Output: 3

Explanation: The answer is "abc", with the length of 3.
## Example 2:

Input: s = "bbbbb"

Output: 1

Explanation: The answer is "b", with the length of 1.
## Example 3:

Input: s = "pwwkew"

Output: 3

Explanation: The answer is "wke", with the length of 3. Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.

# My solution
```python
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        if len(s) == 1:
            return 1
        starting = 0
        moving = 0
        mres = ""
        res = ""
        while starting < len(s):
            if moving <= len(s)-1:
                if s[moving] not in mres:
                    mres += s[moving]
                    moving += 1
                else:
                    starting += 1
                    moving = starting
                    if len(mres) > len(res):
                        res = mres
                    mres = ""   
            else:
                starting += 1
                moving = starting 
        if len(res) > len(mres):
            return len(res)
        else:
            return len(mres)
```

# Fastest solution
```python
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        mx_len, start = 0,0
        used = {}

        for i, char in enumerate(s):
            if char in used and start <= used[char]:
                start = used[char] + 1
            else:
                mx_len = max(mx_len, i-start+1)
            used[char] = i
            
        return mx_len
```
