Location: https://leetcode.com/problems/counting-words-with-a-given-prefix/description/?envType=daily-question&envId=2025-05-07
# Question
You are given an array of strings words and a string pref.

Return the number of strings in words that contain pref as a prefix.

A prefix of a string s is any leading contiguous substring of s.

 
# Example

## Example 1:

Input: words = ["pay","attention","practice","attend"], pref = "at"

Output: 2

Explanation: The 2 strings that contain "at" as a prefix are: "attention" and "attend".

## Example 2:

Input: words = ["leetcode","win","loops","success"], pref = "code"

Output: 0

Explanation: There are no strings that contain "code" as a prefix.

## Constraints:

1 <= words.length <= 100\
1 <= words[i].length, pref.length <= 100\
words[i] and pref consist of lowercase English letters.
 

# My solution 
```python
class Solution(object):
    def prefixCount(self, words, pref):
        """
        :type words: List[str]
        :type pref: str
        :rtype: int
        """
        l = len(pref)
        ans = 0
        for word in words:
            if word[:l]==pref:
                ans += 1
        return ans
        
```
