Location: https://leetcode.com/problems/reverse-vowels-of-a-string/description/?envType=study-plan-v2&envId=leetcode-75

# Question
Given a string s, reverse only all the vowels in the string and return it.

The vowels are 'a', 'e', 'i', 'o', and 'u', and they can appear in both lower and upper cases, more than once.

# Example 

## Example 1:

Input: s = "hello"\
Output: "holle"
## Example 2:

Input: s = "leetcode"\
Output: "leotcede"

# My solution
```python
class Solution(object):
    def reverseVowels(self, s):
        """
        :type s: str
        :rtype: str
        """
        res = ""
        starting = 0
        ending = len(s)-1
        # if len(s)==1:
        #     return s
        while starting <= ending:
            if s[starting].lower() in ['a', 'e', 'i', 'o', 'u'] and s[ending].lower() in ['a', 'e', 'i', 'o', 'u']:
                if starting == ending:
                    res = res[:starting]+s[starting]+res[starting:]
                else:
                    res = res[:starting]+s[ending]+s[starting]+res[starting:]
                starting += 1
                ending -= 1
            elif s[starting].lower() in ['a', 'e', 'i', 'o', 'u']:
                res = res[:starting]+s[ending]+res[starting:]
                ending -= 1
            elif s[ending].lower() in ['a', 'e', 'i', 'o', 'u']:
                res = res[:starting]+s[starting]+res[starting:]
                starting += 1
            else:
                if starting == ending:
                    res = res[:starting]+s[starting]+res[starting:]
                else:
                    res = res[:starting]+s[starting]+s[ending]+res[starting:]
                starting += 1
                ending -= 1
        return res
```

# Fastest solution
```python
class Solution(object):
    def reverseVowels(self, s):
        """
        :type s: str
        :rtype: str
        """
        vowels = set('aeiouAEIOU')
        s = list(s)
        left, right = 0, len(s) - 1
        
        while left < right:
            while left < right and s[left] not in vowels:
                left += 1
            while left < right and s[right] not in vowels:
                right -= 1
                
            if left < right:
                s[left], s[right] = s[right], s[left]
                left += 1
                right -= 1
                
        return ''.join(s)
```
