Location: https://leetcode.com/problems/longest-repeating-character-replacement/description/
# Question
You are given a string s and an integer k. You can choose any character of the string and change it to any other uppercase English character. You can perform this operation at most k times.

Return the length of the longest substring containing the same letter you can get after performing the above operations.

 
# Example

## Example 1:

Input: s = "ABAB", k = 2

Output: 4

Explanation: Replace the two 'A's with two 'B's or vice versa.

## Example 2:

Input: s = "AABABBA", k = 1

Output: 4

Explanation: Replace the one 'A' in the middle with 'B' and form "AABBBBA".\
The substring "BBBB" has the longest repeating letters, which is 4.\
There may exists other ways to achieve this answer too.

## Constraints:

1 <= s.length <= 105\
s consists of only uppercase English letters.\
0 <= k <= s.length
 

# My solution (follows instructions on solutions)
```python
import collections
class Solution(object):
    def characterReplacement(self, s, k):
        """
        :type s: str
        :type k: int
        :rtype: int
        """
        l, r = 0, 0
        ans = -float('inf')
        seen = collections.defaultdict(int)
        max_fre = 0
        while l < len(s) and r < len(s):        
            seen[s[r]] += 1
            max_fre = max(max_fre, max(seen.values()))
            if r-l+1 - max_fre <= k:
                r += 1
            else:
                ans = max(r-l, ans)
                seen[s[l]] -= 1
                seen[s[r]] -= 1
                l += 1
        return max(ans, r-l)
```
