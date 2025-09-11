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
        vowels = 'aeiouAEIOU'
        ans = [st for st in s]
        ind = []
        v = []
        for i, st in enumerate(s):
            if st in vowels:
                ind.append(i)
                v.append(st)
        v = v[::-1]
        for p, i in enumerate(ind):
            ans[i] = v[p]
        return "".join(ans)

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
