Location: https://leetcode.com/problems/number-of-substrings-containing-all-three-characters/description/
# Question
Given a string s consisting only of characters a, b and c.

Return the number of substrings containing at least one occurrence of all these characters a, b and c.

 
# Example

## Example 1:

Input: s = "abcabc"

Output: 10

Explanation: The substrings containing at least one occurrence of the characters a, b and c are "abc", "abca", "abcab", "abcabc", "bca", "bcab", "bcabc", "cab", "cabc" and "abc" (again). 

## Example 2:

Input: s = "aaacb"

Output: 3

Explanation: The substrings containing at least one occurrence of the characters a, b and c are "aaacb", "aacb" and "acb". 

## Example 3:

Input: s = "abc"

Output: 1
 

## Constraints:

3 <= s.length <= 5 x 10^4\
s only consists of a, b or c characters.
 

# My solution (follows instructions on solutions)
```python
import collections
class Solution(object):
    def numberOfSubstrings(self, s):
        """
        :type s: str
        :rtype: int
        """
        l = 0
        ans = 0
        seen = collections.defaultdict(int)
        for r in range(len(s)):
            seen[s[r]] += 1
            while len(seen) == 3:
                ans += len(s) - r
                seen[s[l]] -= 1
                if seen[s[l]] <= 0:
                    seen.pop(s[l])
                l += 1

        # print(sorted(seen))
        # l, r = 0, 0
        # while l < len(s) and r < len(s):
        #     # print(s[l:r+1])
        #     seen[s[r]] += 1
        #     if sorted(seen.keys())==['a','b','c'] and seen['a'] >= 1 and seen['b'] >= 1 and seen['c'] >= 1:
        #         ans += 1
        #     if r < len(s)-1:
        #         r += 1
        #     else:
        #         seen = collections.defaultdict(int)
        #         l += 1
        #         r = l
        #     # print(seen)
        #     # print(ans)
        return ans


```
