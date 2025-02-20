Location: https://leetcode.com/problems/diagonal-traverse-ii/description/
# Question
Given a 2D integer array nums, return all elements of nums in diagonal order as shown in the below images.
 
# Example

## Example 1:

Input: nums = [[1,2,3],[4,5,6],[7,8,9]]

Output: [1,4,2,7,5,3,8,6,9]

## Example 2:

Input: nums = [[1,2,3,4,5],[6,7],[8],[9,10,11],[12,13,14,15,16]]

Output: [1,6,2,8,7,3,9,4,12,10,5,13,11,14,15,16]


Constraints:

1 <= nums.length <= 105\
1 <= nums[i].length <= 105\
1 <= sum(nums[i].length) <= 105\
1 <= nums[i][j] <= 105
 

# My solution (follows hints)
```python
class Solution(object):
    def findDiagonalOrder(self, nums):
        """
        :type nums: List[List[int]]
        :rtype: List[int]
        """
        pq = []
        for i in range(len(nums)):
            for j in range(len(nums[i])):
                heapq.heappush(pq, (i+j, -i, nums[i][j])) # Notice that numbers with equal sums of row and column indexes belong to the same diagonal. Store them in tuples (sum, row, val), sort them, and then regroup the answer.
        ans = []
        for _ in range(len(pq)):
            ind, row, num = heapq.heappop(pq)
            ans.append(num)
        return ans
       
```
