Location: https://leetcode.com/problems/check-if-binary-string-has-at-most-one-segment-of-ones/description/
# Question
Given a binary string s ​​​​​without leading zeros, return true​​​ if s contains at most one contiguous segment of ones. Otherwise, return false. 
# Example

## Example 1:

Input: s = "1001"

Output: false

Explanation: The ones do not form a contiguous segment.

## Example 2:

Input: s = "110"

Output: true

Constraints:

1 <= s.length <= 100\
s[i]​​​​ is either '0' or '1'.\
s[0] is '1'.
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def checkOnesSegment(self, s):
        """
        :type s: str
        :rtype: bool
        """
        found = True
        for i in range(1, len(s)):
            if s[i] ==  "1" and s[i-1] == "0":
                if found:
                    return False
        return found

```
