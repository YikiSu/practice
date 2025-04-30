Location: https://leetcode.com/problems/find-score-of-an-array-after-marking-all-elements/description/?envType=daily-question&envId=2025-04-29
# Question
You are given an array nums consisting of positive integers.

Starting with score = 0, apply the following algorithm:

- Choose the smallest integer of the array that is not marked. If there is a tie, choose the one with the smallest index.
- Add the value of the chosen integer to score.
- Mark the chosen element and its two adjacent elements if they exist.
- Repeat until all the array elements are marked.

Return the score you get after applying the above algorithm.

 
# Example

## Example 1:

Input: nums = [2,1,3,4,5,2]

Output: 7

Explanation: We mark the elements as follows:
- 1 is the smallest unmarked element, so we mark it and its two adjacent elements: [2,1,3,4,5,2].
- 2 is the smallest unmarked element, so we mark it and its left adjacent element: [2,1,3,4,5,2].
- 4 is the only remaining unmarked element, so we mark it: [2,1,3,4,5,2].

Our score is 1 + 2 + 4 = 7.

## Example 2:

Input: nums = [2,3,5,1,3,2]

Output: 5

Explanation: We mark the elements as follows:
- 1 is the smallest unmarked element, so we mark it and its two adjacent elements: [2,3,5,1,3,2].
- 2 is the smallest unmarked element, since there are two of them, we choose the left-most one, so we mark the one at index 0 and its right adjacent element: [2,3,5,1,3,2].
- 2 is the only remaining unmarked element, so we mark it: [2,3,5,1,3,2]

Our score is 1 + 2 + 2 = 5.
 

## Constraints:

1 <= nums.length <= 105\
1 <= nums[i] <= 106
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def findScore(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        ans = 0
        # cnt = {ind:num for ind, num in enumerate(nums)}
        # while cnt:
        #     smallest = min(cnt.values())
        #     ans += smallest
        #     ind = min(cnt.keys(), key=lambda k: cnt[k])
        #     # print(ind)
        #     if ind > 0 and ind-1 in cnt.keys():
        #         cnt.pop(ind-1)
        #     if ind < len(nums)-1 and ind+1 in cnt.keys():
        #         cnt.pop(ind+1)
        #     cnt.pop(ind)
        # return ans
        stack = []
        for ind, num in enumerate(nums):
            heapq.heappush(stack, (num, ind))
        marked = [False]*len(nums)
        while stack:
            min_, ind = heapq.heappop(stack)
            if not marked[ind]:
                ans += min_
                if ind > 0:
                    marked[ind-1] = True
                if ind < len(nums) - 1:
                    marked[ind+1] = True
        return ans
```
