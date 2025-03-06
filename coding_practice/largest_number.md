Location: https://leetcode.com/problems/largest-number/description/
# Question
Given a list of non-negative integers nums, arrange them such that they form the largest number and return it.

Since the result may be very large, so you need to return a string instead of an integer.

 
# Example

## Example 1:

Input: nums = [10,2]

Output: "210"

## Example 2:

Input: nums = [3,30,34,5,9]

Output: "9534330"
 
## Constraints:

1 <= nums.length <= 100\
0 <= nums[i] <= 109
 

# My solution (follows instructions on solutions)
```python
import collections
class Solution(object):
    def largestNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: str
        """
        l = collections.defaultdict(list)
        for num in nums:
            s = str(num)
            l[s[0]].append(str(num))
        # print(l)
        ans = ""
        for key in sorted(l, reverse=True):
            num = sorted(l[key], reverse=True, key=lambda x: x*10)
            curr = ""
            while num:
                c = num.pop()
                if c+curr > curr+c:
                    curr = c+curr
                else:
                    curr += c
            ans += curr
        return ans if int(ans) != 0 else "0"
```
