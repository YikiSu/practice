Location: https://leetcode.com/problems/longest-happy-string/description/
# Question
A string s is called happy if it satisfies the following conditions:

- s only contains the letters 'a', 'b', and 'c'.
- s does not contain any of "aaa", "bbb", or "ccc" as a substring.
- s contains at most a occurrences of the letter 'a'.
- s contains at most b occurrences of the letter 'b'.
- s contains at most c occurrences of the letter 'c'.

Given three integers a, b, and c, return the longest possible happy string. If there are multiple longest happy strings, return any of them. If there is no such string, return the empty string "".

A substring is a contiguous sequence of characters within a string.

 
# Example

## Example 1:

Input: a = 1, b = 1, c = 7

Output: "ccaccbcc"

Explanation: "ccbccacc" would also be a correct answer.

## Example 2:

Input: a = 7, b = 1, c = 0

Output: "aabaa"

Explanation: It is the only correct answer in this case.


Constraints:

0 <= a, b, c <= 100\
a + b + c > 0
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def longestDiverseString(self, a, b, c):
        """
        :type a: int
        :type b: int
        :type c: int
        :rtype: str
        """
        pq = []
        if a > 0:
            heapq.heappush(pq, (-a, "a"))
        if b > 0:
            heapq.heappush(pq, (-b, "b"))
        if c > 0:
            heapq.heappush(pq, (-c, "c"))
        
        ans = ""
        while pq:
            cnt1, st1 = heapq.heappop(pq)
            if len(ans) >= 2 and ans[-1] == st1 and ans[-2] == st1:
                if not pq:
                    break
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
        return ans

        
```
