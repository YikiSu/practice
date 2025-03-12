Location: https://leetcode.com/problems/take-k-of-each-character-from-left-and-right/description/
# Question
You are given a string s consisting of the characters 'a', 'b', and 'c' and a non-negative integer k. Each minute, you may take either the leftmost character of s, or the rightmost character of s.

Return the minimum number of minutes needed for you to take at least k of each character, or return -1 if it is not possible to take k of each character.

 
# Example

## Example 1:

Input: s = "aabaaaacaabc", k = 2

Output: 8

Explanation: \
Take three characters from the left of s. You now have two 'a' characters, and one 'b' character.\
Take five characters from the right of s. You now have four 'a' characters, two 'b' characters, and two 'c' characters.\
A total of 3 + 5 = 8 minutes is needed.\
It can be proven that 8 is the minimum number of minutes needed.

## Example 2:

Input: s = "a", k = 1

Output: -1

Explanation: It is not possible to take one 'b' or 'c' so return -1.
 

## Constraints:

1 <= s.length <= 105\
s consists of only the letters 'a', 'b', and 'c'.\
0 <= k <= s.length
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def takeCharacters(self, s, k):
        """
        :type s: str
        :type k: int
        :rtype: int
        """
        ans = float('inf')
        a,b,c = 0,0,0
        l,r = 0,0
        cnt = collections.Counter(s)
        if cnt['a'] < k or cnt['b'] < k or cnt['c'] < k:
            return -1
        n = len(s)
        while r < n:
            if s[r] == 'a': a += 1
            if s[r] == 'b': b+=1
            if s[r] == 'c': c+=1
            r += 1
            while a > cnt['a']-k or b>cnt['b']-k or c>cnt['c']-k:
                if s[l] == 'a': a-=1
                if s[l] == 'b': b-=1
                if s[l] == 'c': c-=1
                l += 1
            ans = min(ans, n-(r-l))
        return ans
```
