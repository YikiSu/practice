Location: https://leetcode.com/problems/maximum-consecutive-floors-without-special-floors/description/
# Question
Alice manages a company and has rented some floors of a building as office space. Alice has decided some of these floors should be special floors, used for relaxation only.

You are given two integers bottom and top, which denote that Alice has rented all the floors from bottom to top (inclusive). You are also given the integer array special, where special[i] denotes a special floor that Alice has designated for relaxation.

Return the maximum number of consecutive floors without a special floor.

 
# Example

## Example 1:

Input: bottom = 2, top = 9, special = [4,6]

Output: 3

Explanation: The following are the ranges (inclusive) of consecutive floors without a special floor:
- (2, 3) with a total amount of 2 floors.
- (5, 5) with a total amount of 1 floor.
- (7, 9) with a total amount of 3 floors.\
Therefore, we return the maximum number which is 3 floors.

## Example 2:

Input: bottom = 6, top = 8, special = [7,6,8]

Output: 0

Explanation: Every floor rented is a special floor, so we return 0.

## Constraints:

1 <= special.length <= 105\
1 <= bottom <= special[i] <= top <= 109\
All the values of special are unique.
 

# My solution 
```python
class Solution(object):
    def maxConsecutive(self, bottom, top, special):
        """
        :type bottom: int
        :type top: int
        :type special: List[int]
        :rtype: int
        """
        # special = sorted(special)
        # ans = 0
        # curr = 0
        # for floor in range(bottom, top+1):
        #     if len(special) == 0:
        #         ans = max(ans, top-floor+1)
        #         break
        #     if floor != special[0]:
        #         curr += 1
        #     else:
        #         special = special[1:]
        #         ans = max(ans, curr)
        #         curr = 0
        # return ans
        curr = bottom
        special = sorted(special)
        last = special[-1]
        ans = 0
        for floor in special:
            if curr != floor:
                ans = max(ans, floor-curr)
                curr = floor + 1
            else:
                curr += 1
        if top > last:
            ans = max(ans, top-last)
        return ans
```
