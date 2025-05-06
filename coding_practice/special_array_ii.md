Location: https://leetcode.com/problems/special-array-ii/description/?envType=daily-question&envId=2025-05-05
# Question
An array is considered special if every pair of its adjacent elements contains two numbers with different parity.

You are given an array of integer nums and a 2D integer matrix queries, where for queries[i] = [fromi, toi] your task is to check that subarray nums[fromi..toi] is special or not.

Return an array of booleans answer such that answer[i] is true if nums[fromi..toi] is special.
 
# Example

## Example 1:

Input: nums = [3,4,1,2,6], queries = [[0,4]]

Output: [false]

Explanation:

The subarray is [3,4,1,2,6]. 2 and 6 are both even.

## Example 2:

Input: nums = [4,3,1,6], queries = [[0,2],[2,3]]

Output: [false,true]

Explanation:

The subarray is [4,3,1]. 3 and 1 are both odd. So the answer to this query is false.\
The subarray is [1,6]. There is only one pair: (1,6) and it contains numbers with different parity. So the answer to this query is true.

## Constraints:

1 <= nums.length <= 105\
1 <= nums[i] <= 105\
1 <= queries.length <= 105\
queries[i].length == 2\
0 <= queries[i][0] <= queries[i][1] <= nums.length - 1
 

# My solution (follows instructions on solutions)
```python
from functools import reduce
import operator
class Solution(object):
    def isArraySpecial(self, nums, queries):
        """
        :type nums: List[int]
        :type queries: List[List[int]]
        :rtype: List[bool]
        """
        stack = [0]
        for i in range(1, len(nums)):
            # stack.append((nums[i]%2!=nums[i-1]%2)*1)
            if nums[i]%2 != nums[i-1]%2:
                stack.append(stack[-1])
            else:
                stack.append(stack[-1]+1)
        ans = []
        for q in queries:
            if stack[q[0]] != stack[q[1]]:
                ans.append(False)
            else:
                ans.append(True)
        return ans
        # ans = []
        # for q in queries:
        #     ans.append(1==reduce(operator.mul, stack[q[0]:q[1]], 1))
        return stack
```
