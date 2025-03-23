Location: https://leetcode.com/problems/maximum-score-from-removing-substrings/description/
# Question
You are given a string s and two integers x and y. You can perform two types of operations any number of times.

- Remove substring "ab" and gain x points.
  - For example, when removing "ab" from "cabxbae" it becomes "cxbae".
- Remove substring "ba" and gain y points.
  - For example, when removing "ba" from "cabxbae" it becomes "cabxe".

Return the maximum points you can gain after applying the above operations on s.

 
# Example

## Example 1:

Input: s = "cdbcbbaaabab", x = 4, y = 5

Output: 19

Explanation:
- Remove the "ba" underlined in "cdbcbbaaabab". Now, s = "cdbcbbaaab" and 5 points are added to the score.
- Remove the "ab" underlined in "cdbcbbaaab". Now, s = "cdbcbbaa" and 4 points are added to the score.
- Remove the "ba" underlined in "cdbcbbaa". Now, s = "cdbcba" and 5 points are added to the score.
- Remove the "ba" underlined in "cdbcba". Now, s = "cdbc" and 5 points are added to the score.\
Total score = 5 + 4 + 5 + 5 = 19.

## Example 2:

Input: s = "aabbaaxybbaabb", x = 5, y = 4

Output: 20

## Constraints:

1 <= s.length <= 105\
1 <= x, y <= 104\
s consists of lowercase English letters.
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def maximumGain(self, s, x, y):
        """
        :type s: str
        :type x: int
        :type y: int
        :rtype: int
        """
        if len(s) <=1:
            return 0
        if x > y:
            first = "ab"
            second = "ba"
            l,r = x, y
        else:
            first = "ba"
            second = "ab"
            l,r = y, x
        starting = 1
        stack = [s[0]]
        ans = 0
        while starting < len(s):
            # print(stack)
            if stack and (s[starting] == first[-1] and stack[-1]+s[starting] == first):
                stack.pop(-1)
                ans += l
            else:
                stack.append(s[starting])
            starting += 1
        if stack:
            stack2 = [stack[0]]
            starting2 = 1
            while starting2 < len(stack):
                if stack2 and (stack[starting2] == second[-1] and stack2[-1]+stack[starting2] == second):
                    stack2.pop(-1)
                    ans += r
                else:
                    stack2.append(stack[starting2])
                starting2 += 1
        return ans
```
