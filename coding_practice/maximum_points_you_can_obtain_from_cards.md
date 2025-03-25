Location: https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/description/
# Question
There are several cards arranged in a row, and each card has an associated number of points. The points are given in the integer array cardPoints.

In one step, you can take one card from the beginning or from the end of the row. You have to take exactly k cards.

Your score is the sum of the points of the cards you have taken.

Given the integer array cardPoints and the integer k, return the maximum score you can obtain.
# Example

## Example 1:

Input: cardPoints = [1,2,3,4,5,6,1], k = 3

Output: 12

Explanation: After the first step, your score will always be 1. However, choosing the rightmost card first will maximize your total score. The optimal strategy is to take the three cards on the right, giving a final score of 1 + 6 + 5 = 12.

## Example 2:

Input: cardPoints = [2,2,2], k = 2

Output: 4

Explanation: Regardless of which two cards you take, your score will always be 4.

## Example 3:

Input: cardPoints = [9,7,7,9,7,7,9], k = 7

Output: 55

Explanation: You have to take all the cards. Your score is the sum of points of all cards.
 

## Constraints:

1 <= cardPoints.length <= 105\
1 <= cardPoints[i] <= 104\
1 <= k <= cardPoints.length
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def maxScore(self, cardPoints, k):
        """
        :type cardPoints: List[int]
        :type k: int
        :rtype: int
        """
        ans = 0
        if len(cardPoints) == k:
            return sum(cardPoints)
        n = len(cardPoints)
        total = sum(cardPoints)
        window = n-k
        cur_sum = sum(cardPoints[:window])
        min_subarray = sum(cardPoints[:window])
        for i in range(window, n):
            cur_sum += cardPoints[i]-cardPoints[i-window]
            min_subarray = min(cur_sum, min_subarray)
        return total - min_subarray

        # while l >=0:
        #     # print(l)
        #     # print(cardPoints[-(k-l):])
        #     if l == k:
        #         ans = max(sum(cardPoints[:l]), ans)
        #     else:
        #         ans = max(sum(cardPoints[:l]+cardPoints[-(k-l):]), ans)
        #     l -= 1
        # return ans


        
```
