Location: https://leetcode.com/problems/largest-time-for-given-digits/description/
# Question
Given an array arr of 4 digits, find the latest 24-hour time that can be made using each digit exactly once.

24-hour times are formatted as "HH:MM", where HH is between 00 and 23, and MM is between 00 and 59. The earliest 24-hour time is 00:00, and the latest is 23:59.

Return the latest 24-hour time in "HH:MM" format. If no valid time can be made, return an empty string.

# Example

## Example 1:

Input: arr = [1,2,3,4]

Output: "23:41"

Explanation: The valid 24-hour times are "12:34", "12:43", "13:24", "13:42", "14:23", "14:32", "21:34", "21:43", "23:14", and "23:41". Of these times, "23:41" is the latest.

## Example 2:

Input: arr = [5,5,5,5]

Output: ""

Explanation: There are no valid 24-hour times as "55:55" is not valid.

## Constraints:

arr.length == 4
0 <= arr[i] <= 9
 

# My solution 
```python
import itertools
class Solution(object):
    def largestTimeFromDigits(self, arr):
        """
        :type arr: List[int]
        :rtype: str
        """
        combos = [st for st in itertools.permutations(arr) if st[0]*10+st[1]<24 and st[2]*10+st[3]<60]
        ans = ""
        max_ = -float('inf')
        for combo in combos:
            # print(combo)
            if combo[0]*1000+combo[1]*100+combo[2]*10+combo[3] >= 2400:
                curr = -float("inf")
            # if combo[0]*10+combo[1] == 24:
            #     # curr = combo[2]*10+combo[3]
            #     pass
            else:
                curr = (combo[0]*10+combo[1])*60+(combo[2]*10+combo[3])
            # print(curr)
            if curr > max_:
                ans = str(combo[0])+str(combo[1])+":"+str(combo[2])+str(combo[3])
                max_ = curr
        return ans
                
```
