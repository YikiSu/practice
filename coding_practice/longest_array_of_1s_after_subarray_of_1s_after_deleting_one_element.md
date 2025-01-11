Location: https://leetcode.com/problems/longest-subarray-of-1s-after-deleting-one-element/description/?envType=study-plan-v2&envId=leetcode-75

# Question
Given a binary array nums, you should delete one element from it.

Return the size of the longest non-empty subarray containing only 1's in the resulting array. Return 0 if there is no such subarray.

# Example
## Example 1:

Input: nums = [1,1,0,1]

Output: 3

Explanation: After deleting the number in position 2, [1,1,1] contains 3 numbers with value of 1's.


## Example 2:

Input: nums = [0,1,1,1,0,1,1,0,1]

Output: 5

Explanation: After deleting the number in position 4, [0,1,1,1,1,1,0,1] longest subarray with value of 1's is [1,1,1,1,1].

## Example 3:

Input: nums = [1,1,1]

Output: 2

Explanation: You must delete one element.
 
# Constraints
- 1 <= nums.length <= 105
- nums[i] is either 0 or 1.

# My solution (Followed instructions of others)
```python
class Solution(object):
    def longestSubarray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        l, r, n = 0, 0, len(nums)
        ans = 0
        cnt0 = 0
        while r < n:
            if nums[r] == 0:
                cnt0 += 1
            while l < n and cnt0 == 2:
                if nums[l] == 0:
                    cnt0 -= 1
                l += 1
            ans = max(r-l, ans)
            r += 1

        return ans
            
```
# Logic
**Sliding Window Technique:**
1. Initialize two pointers i and j to track the start and end indices of the subarray, respectively. Also, initialize variables n as the size of the input array nums, c0 as the count of zeros encountered so far, and mx as the maximum length of the subarray.

2. Start iterating over the array using the j pointer until it reaches the end (n). For each element nums[j]:
- If the current element is zero (nums[j] == 0), increment the count of zeros (c0++).
3. Enter a nested while loop with the condition while (i < n && c0 == 2) to handle the case when there are more than one zeros in the current subarray.
- Check from element at the start index (nums[i]) is zero (nums[i] == 0).
- If it is zero, decrement the count of zeros (c0--) to indicate that we have removed one zero from the subarray.
- Increment the start index (i++) to shrink the subarray from the left side.we will strink until count of zeroes becomes less than 2
4. Calculate the length of the current subarray (j - i) and update the maximum length (mx) if necessary.
5. Increment the j pointer to move the sliding window to the right for the next iteration.
6. Repeat steps 2-5 until we have iterated over the entire array.
7. Return the maximum length of the subarray (mx) as the result.
