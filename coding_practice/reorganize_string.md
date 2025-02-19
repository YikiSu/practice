Location: https://leetcode.com/problems/reorganize-string/description/
# Question
Given a string s, rearrange the characters of s so that any two adjacent characters are not the same.

Return any possible rearrangement of s or return "" if not possible.
 
# Example

## Example 1:

Input: s = "aab"

Output: "aba"

## Example 2:

Input: s = "aaab"

Output: ""

Constraints:

1 <= s.length <= 500\
s consists of lowercase English letters.
 

# My solution 
```python
import collections
class Solution(object):
    def reorganizeString(self, s):
        """
        :type s: str
        :rtype: str
        """
        pq = []
        cnt = collections.Counter(s)
        for key, val in cnt.items():
            heapq.heappush(pq, (-val, key))
        ans = ""
        while pq:
            cnt1, st1 = heapq.heappop(pq)
            if len(ans) >= 1 and st1 == ans[-1]:
                if not pq and cnt1 < 0:
                    return ""
                else:
                    cnt2, st2 = heapq.heappop(pq)
                    ans += st2
                    cnt2 += 1
                    if cnt2 < 0:
                        heapq.heappush(pq, (cnt2, st2))
                    heapq.heappush(pq, (cnt1, st1))
            else:
                ans += st1
                cnt1 += 1
                if cnt1 < 0:
                        heapq.heappush(pq, (cnt1, st1))
        if pq:
            return ""
        else:
            return ans
        
```
