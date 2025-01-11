Location: https://leetcode.com/problems/max-consecutive-ones-iii/description/?envType=study-plan-v2&envId=leetcode-75

# Question
Given a binary array nums and an integer k, return the maximum number of consecutive 1's in the array if you can flip at most k 0's.

# Example
## Example 1:

Input: nums = [1,1,1,0,0,0,1,1,1,1,0], k = 2

Output: 6

Explanation: [1,1,1,0,0,1,1,1,1,1,1] Bolded numbers were flipped from 0 to 1. The longest subarray is underlined.


## Example 2:

Input: nums = [0,0,1,1,0,0,1,1,1,0,1,1,0,0,0,1,1,1,1], k = 3

Output: 10

Explanation: [0,0,1,1,1,1,1,1,1,1,1,1,0,0,0,1,1,1,1]
Bolded numbers were flipped from 0 to 1. The longest subarray is underlined.
 
# Constraints
- 1 <= nums.length <= 105
- nums[i] is either 0 or 1.
- 0 <= k <= nums.length

# My solution (Followed instructions of others)
```python
class Solution(object):
    def longestOnes(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """
        left, right = 0, 0
        while right < len(nums):
            if nums[right] == 0:
                k -= 1
            right += 1
            if k < 0:
                if nums[left] == 0:
                    k += 1
                left += 1
        return right - left
```
# Logic
1. Sliding Window Technique:
- We will use two pointers, i and j, both initially set to 0. j will expand the window to the right, and i will contract the window from the left when the number of zeros exceeds k.
- The variable k will track how many zeros can be included in the current window.
- We will iterate through the array with the pointer j and, whenever we encounter a 0, we decrement k. If k becomes negative, it means the current window has more than k zeros, so we need to move i to the right (contract the window) and possibly increment k back if we remove a zero.
- During this process, we keep track of the maximum window length, which is the longest subarray found.

2. Steps:
- Start with two pointers i = 0 and j = 0 and a variable to track the number of zeros in the current window.
- Move j and expand the window to the right.
- When a zero is encountered, decrement k.
- If k becomes negative, increment i to shrink the window until k becomes non-negative again.
- The result will be the maximum length of a valid window.
