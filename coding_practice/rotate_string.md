Location: https://leetcode.com/problems/rotate-string/description/
# Question
Given two strings s and goal, return true if and only if s can become goal after some number of shifts on s.

A shift on s consists of moving the leftmost character of s to the rightmost position.

For example, if s = "abcde", then it will be "bcdea" after one shift.

 
# Example

## Example 1:

Input: s = "abcde", goal = "cdeab"

Output: true

## Example 2:

Input: s = "abcde", goal = "abced"

Output: false

## Constraints:

1 <= s.length, goal.length <= 100\
s and goal consist of lowercase English letters.
 

# My solution 
```python
class Solution(object):
    def rotateString(self, s, goal):
        """
        :type s: str
        :type goal: str
        :rtype: bool
        """
        # l = 0
        if len(s) != len(goal):
            return False
        # while l < len(s):
        #     if s[0] == goal[l]:
        #         goal_curr = goal[l:]+goal[:l]
        #         return s == goal_curr
        #     else:
        #         l += 1
        # return False
        l = len(goal)-1
        while l >= 0:
            print(l)
            if s[0] == goal[l]:
                goal_curr = goal[l:]+goal[:l]
                if s == goal_curr:
                    return True
            l -= 1
        return False
```
