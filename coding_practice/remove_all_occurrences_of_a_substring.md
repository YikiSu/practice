Location: https://leetcode.com/problems/remove-all-occurrences-of-a-substring/description/?envType=daily-question&envId=2025-04-30
# Question
Given two strings s and part, perform the following operation on s until all occurrences of the substring part are removed:

Find the leftmost occurrence of the substring part and remove it from s.

Return s after removing all occurrences of part.

A substring is a contiguous sequence of characters in a string.

 
# Example

## Example 1:

Input: s = "daabcbaabcbc", part = "abc"

Output: "dab"

Explanation: The following operations are done:
- s = "daabcbaabcbc", remove "abc" starting at index 2, so s = "dabaabcbc".
- s = "dabaabcbc", remove "abc" starting at index 4, so s = "dababc".
- s = "dababc", remove "abc" starting at index 3, so s = "dab".

Now s has no occurrences of "abc".

## Example 2:

Input: s = "axxxxyyyyb", part = "xy"

Output: "ab"

Explanation: The following operations are done:
- s = "axxxxyyyyb", remove "xy" starting at index 4 so s = "axxxyyyb".
- s = "axxxyyyb", remove "xy" starting at index 3 so s = "axxyyb".
- s = "axxyyb", remove "xy" starting at index 2 so s = "axyb".
- s = "axyb", remove "xy" starting at index 1 so s = "ab".

Now s has no occurrences of "xy".

## Constraints:

1 <= s.length <= 1000\
1 <= part.length <= 1000\
s​​​​​​ and part consists of lowercase English letters.
 

# My solution
```python
class Solution(object):
    def removeOccurrences(self, s, part):
        """
        :type s: str
        :type part: str
        :rtype: str
        """
        ans = ""
        l, r = 0, 1
        for st in s:
            ans += st
            # print(st)
            if st == part[-1]:
                # print('entering')
                # print(ans[-len(part):])
                # print(part)
                if len(ans) >= len(part) and ans[-len(part):] == part:
                    # print(ans[:-len(part)])
                    ans = ans[:-len(part)]
        return ans
        
```
