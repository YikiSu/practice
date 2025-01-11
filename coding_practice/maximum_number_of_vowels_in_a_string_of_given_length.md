Location: https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/description/?envType=study-plan-v2&envId=leetcode-75

# Question
Given a string s and an integer k, return the maximum number of vowel letters in any substring of s with length k.

Vowel letters in English are 'a', 'e', 'i', 'o', and 'u'.

 # Example

## Example 1:

- Input: s = "abciiidef", k = 3
- Output: 3
- Explanation: The substring "iii" contains 3 vowel letters.
## Example 2:

- Input: s = "aeiou", k = 2
- Output: 2
- Explanation: Any substring of length 2 contains 2 vowels.

## Example 3:

- Input: s = "leetcode", k = 3
- Output: 2
- Explanation: "lee", "eet" and "ode" contain 2 vowels.
 

# Constraints:
- 1 <= s.length <= 105
- s consists of lowercase English letters.
- 1 <= k <= s.length

# My solution (follow instructions of others)
```python
class Solution(object):
    def maxVowels(self, s, k):
        """
        :type s: str
        :type k: int
        :rtype: int
        """
        cnt = 0
        ans = 0
        for i in range(k):
            if s[i] in ['a', 'e', 'i', 'o', 'u']:
                cnt += 1
        ans = cnt
        for i in range(k, len(s)):
            if s[i] in ['a', 'e', 'i', 'o', 'u']:
                cnt += 1
            if s[i-k] in ['a', 'e', 'i', 'o', 'u']:
                cnt -= 1
            ans = max(ans, cnt)
        return ans

```
