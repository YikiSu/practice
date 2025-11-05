Location: https://leetcode.com/problems/make-array-zero-by-subtracting-equal-amounts/description/
# Question
You are given a non-negative integer array nums. In one operation, you must:

Choose a positive integer x such that x is less than or equal to the smallest non-zero element in nums.\
Subtract x from every positive element in nums.

Return the minimum number of operations to make every element in nums equal to 0.

 
# Example

## Example 1:

Input: nums = [1,5,0,3,5]

Output: 3

Explanation:\
In the first operation, choose x = 1. Now, nums = [0,4,0,2,4].\
In the second operation, choose x = 2. Now, nums = [0,2,0,0,2].\
In the third operation, choose x = 2. Now, nums = [0,0,0,0,0].

## Example 2:

Input: nums = [0]

Output: 0

Explanation: Each element in nums is already 0 so no operations are needed.

## Constraints:

1 <= nums.length <= 100\
0 <= nums[i] <= 100
 

# My solution 
```python
class Solution(object):
    def minimumOperations(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        cnt = sum([1 for num in nums if num != 0])
        if cnt == 0:
            return 0
        ans = 0
        while cnt:
            ans += 1
            x = min([num for num in nums if num!=0])
            for ind, num in enumerate(nums):
                if num != 0:
                    nums[ind] = num-x
                    if num - x == 0:
                        cnt -= 1
        return ans
```
