Location: https://leetcode.com/problems/shifting-letters-ii/description/?envType=daily-question&envId=2025-05-25
# Question
You are given a string s of lowercase English letters and a 2D integer array shifts where shifts[i] = [starti, endi, directioni]. For every i, shift the characters in s from the index starti to the index endi (inclusive) forward if directioni = 1, or shift the characters backward if directioni = 0.

Shifting a character forward means replacing it with the next letter in the alphabet (wrapping around so that 'z' becomes 'a'). Similarly, shifting a character backward means replacing it with the previous letter in the alphabet (wrapping around so that 'a' becomes 'z').

Return the final string after all such shifts to s are applied.

 
# Example

## Example 1:

Input: s = "abc", shifts = [[0,1,0],[1,2,1],[0,2,1]]

Output: "ace"

Explanation: Firstly, shift the characters from index 0 to index 1 backward. Now s = "zac".\
Secondly, shift the characters from index 1 to index 2 forward. Now s = "zbd".\
Finally, shift the characters from index 0 to index 2 forward. Now s = "ace".

## Example 2:

Input: s = "dztz", shifts = [[0,0,0],[1,1,1]]

Output: "catz"

Explanation: Firstly, shift the characters from index 0 to index 0 backward. Now s = "cztz".\
Finally, shift the characters from index 1 to index 1 forward. Now s = "catz".

## Constraints:

1 <= s.length, shifts.length <= 5 * 104\
shifts[i].length == 3\
0 <= starti <= endi < s.length\
0 <= directioni <= 1\
s consists of lowercase English letters.
 

# My solution (follows instructions on solutions)
```python
import collections
class Solution(object):
    def shiftingLetters(self, s, shifts):
        """
        :type s: str
        :type shifts: List[List[int]]
        :rtype: str
        """
        diff = [0]*(len(s)+1)
        ans = [st for st in s]
        # print(ans)
        for shift in shifts:
            direction = 1 if shift[2] else -1
            diff[shift[0]] += direction
            if shift[1]+1 < len(s):
                diff[shift[1]+1] += (-1)*direction
        total_shifts = 0
        for ind in range(len(s)):
            total_shifts += diff[ind]
            curr = ord(ans[ind])-ord('a')
            new = (curr+total_shifts)%26
            if new < 0:
                new += 26
            ans[ind] = chr(ord('a')+new)
        return "".join(ans)
        # ans = s
        # for shift in shifts:
        #     curr = ans[:shift[0]]
        #     if shift[2] == 0:
        #         direction = -1
        #     else:
        #         direction = 1
        #     for ind in range(shift[0], shift[1]+1):
        #         if ans[ind] == "z" and direction == 1:
        #             curr += "a"
        #         elif ans[ind] == 'a' and direction == -1:
        #             curr += 'z'
        #         else:
        #             curr += chr(ord(ans[ind])+direction)
        #     if shift[1] < len(s)-1:
        #         curr += ans[shift[1]+1:]
        #     ans = curr
        # return ans
```
