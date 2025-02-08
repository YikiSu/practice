Location: https://leetcode.com/problems/zigzag-conversion/description/?envType=problem-list-v2&envId=string
# Question
The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

P   A   H   N
A P L S I I G
Y   I   R
And then read line by line: "PAHNAPLSIIGYIR"

Write the code that will take a string and make this conversion given a number of rows:

string convert(string s, int numRows);

 
# Example

## Example 1:

Input: s = "PAYPALISHIRING", numRows = 3

Output: "PAHNAPLSIIGYIR"

## Example 2:

Input: s = "PAYPALISHIRING", numRows = 4

Output: "PINALSIGYAHRPI"

Explanation: 
P     I    N
A   L S  I G
Y A   H R
P     I

## Example 3:

Input: s = "A", numRows = 1

Output: "A"

Constraints:

1 <= s.length <= 1000\
s consists of English letters (lower-case and upper-case), ',' and '.'.\
1 <= numRows <= 1000
 

# My solution (uses chatgpt to fix)
```python
class Solution(object):
    def convert(self, s, numRows):
        """
        :type s: str
        :type numRows: int
        :rtype: str
        """
        ans = [[""] for _ in range(numRows)]
        row_cnt = 0
        direction = -1
        if len(s) <= 1 or numRows >= len(s) or numRows == 1: return s
        for i in range(len(s)):
            print(row_cnt)
            ans[row_cnt].append(s[i])
            if row_cnt == 0 or row_cnt == numRows-1:
                direction *= -1
            row_cnt += direction
        return "".join(["".join(s) for s in ans])
```
