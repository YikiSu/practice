Location: https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/description/
# Question
You are given a string s consisting of lowercase English letters. A duplicate removal consists of choosing two adjacent and equal letters and removing them.

We repeatedly make duplicate removals on s until we no longer can.

Return the final string after all such duplicate removals have been made. It can be proven that the answer is unique.
# Example

## Example 1:

Input: s = "abbaca"

Output: "ca"

Explanation: \
For example, in "abbaca" we could remove "bb" since the letters are adjacent and equal, and this is the only possible move.  The result of this move is that the string is "aaca", of which only "aa" is possible, so the final string is "ca".

## Example 2:

Input: s = "azxxzy"

Output: "ay"

## Constraints:

1 <= s.length <= 105\
s consists of lowercase English letters.
 

# My solution 
```python
class Solution(object):
    def removeDuplicates(self, s):
        """
        :type s: str
        :rtype: str
        """
        ans = ""
        for st in s:
            if not ans or ans[-1] != st:
                ans += st
            elif ans[-1] == st:
                ans = ans[:-1]
        return ans
```
