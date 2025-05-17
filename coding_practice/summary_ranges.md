Location: https://leetcode.com/problems/summary-ranges/description/?envType=problem-list-v2&envId=array
# Question
You are given a sorted unique integer array nums.

A range [a,b] is the set of all integers from a to b (inclusive).

Return the smallest sorted list of ranges that cover all the numbers in the array exactly. That is, each element of nums is covered by exactly one of the ranges, and there is no integer x such that x is in one of the ranges but not in nums.

Each range [a,b] in the list should be output as:

- "a->b" if a != b
- "a" if a == b

 
# Example

## Example 1:

Input: nums = [0,1,2,4,5,7]

Output: ["0->2","4->5","7"]

Explanation: The ranges are:\
[0,2] --> "0->2"\
[4,5] --> "4->5"\
[7,7] --> "7"
## Example 2:

Input: nums = [0,2,3,4,6,8,9]

Output: ["0","2->4","6","8->9"]

Explanation: The ranges are:\
[0,0] --> "0"\
[2,4] --> "2->4"\
[6,6] --> "6"\
[8,9] --> "8->9"

## Constraints:

0 <= nums.length <= 20\
-231 <= nums[i] <= 231 - 1\
All the values of nums are unique.\
nums is sorted in ascending order.
 

# My solution 
```python
class Solution(object):
    def summaryRanges(self, nums):
        """
        :type nums: List[int]
        :rtype: List[str]
        """
        ans = []
        l, r = "", ""
        for ind, num in enumerate(nums):
            if ind == 0:
                l = str(num)
            elif num == nums[ind-1]+1:
                r = str(num)
            else:
                if r != "":
                    ans.append(l+"->"+r)
                else:
                    ans.append(l)
                l, r = str(num), ""
        if l != "":
            if r  != "":
                ans.append(l+"->"+r)
            else:
                ans.append(l)

        return ans
```
