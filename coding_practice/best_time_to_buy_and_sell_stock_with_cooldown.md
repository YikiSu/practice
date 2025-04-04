Location: https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/
# Question
You are given an array prices where prices[i] is the price of a given stock on the ith day.

Find the maximum profit you can achieve. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times) with the following restrictions:

- After you sell your stock, you cannot buy stock on the next day (i.e., cooldown one day).

Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).
 
# Example

## Example 1:

Input: prices = [1,2,3,0,2]

Output: 3

Explanation: transactions = [buy, sell, cooldown, buy, sell]

## Example 2:

Input: prices = [1]

Output: 0

## Constraints:
1 <= prices.length <= 5000\
0 <= prices[i] <= 1000

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        # dp = [0]*len(prices)
        # for ind in range(len(prices)-1, 0, -1):
        #     if dp[ind] !=-float('inf') and prices[ind]-prices[ind-1]>0:
        #         dp[ind] = prices[ind]-prices[ind-1]
        #         dp[ind-1] = -float('inf')
        # return sum([num for num in dp if num != -float('inf')])
        hold = [0]*len(prices)
        sell = [0]*len(prices)
        cooldown = [0]*len(prices)
        hold[0] = -prices[0]
        for i in range(1, len(prices)):
            hold[i] = max(hold[i-1], cooldown[i-1]-prices[i])
            sell[i] = hold[i-1] + prices[i]
            cooldown[i] = max(cooldown[i-1], sell[i-1])
        return max(sell[-1], cooldown[-1])
```
