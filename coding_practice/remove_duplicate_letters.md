Location: https://leetcode.com/problems/remove-duplicate-letters/description/?envType=problem-list-v2&envId=monotonic-stack
# Question
Given a string s, remove duplicate letters so that every letter appears once and only once. You must make sure your result is 
the smallest in lexicographical order among all possible results.
# Example

## Example 1:

Input: s = "bcabc"

Output: "abc"

## Example 2:

Input: s = "cbacdcbc"

Output: "acdb"


Constraints:

1 <= s.length <= 104\
s consists of lowercase English letters.
 

# My solution (follows hints on ChatGPT)
```python
import collections
class Solution(object):
    def removeDuplicateLetters(self, s):
        """
        :type s: str
        :rtype: str
        """
        stack = []
        seen = set()
        cnt = collections.Counter(s)
        for st in s:
            if not stack:
                stack.append(st)
                seen.add(st)
                cnt[st] -= 1
            elif st not in seen:
                while stack:
                    if st < stack[-1] and cnt[stack[-1]] > 0:
                        pre = stack.pop()
                        seen.remove(pre)
                    else:
                        break
                stack.append(st)
                seen.add(st)
                cnt[st] -= 1
            else:
                cnt[st] -= 1
        return "".join(stack)

       
```
