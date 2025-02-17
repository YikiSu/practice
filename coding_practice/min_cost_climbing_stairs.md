Location: https://leetcode.com/problems/min-cost-climbing-stairs/description/?envType=study-plan-v2&envId=leetcode-75
# Question
You are given an integer array cost where cost[i] is the cost of ith step on a staircase. Once you pay the cost, you can either climb one or two steps.

You can either start from the step with index 0, or the step with index 1.

Return the minimum cost to reach the top of the floor.

# Example
## Example 1:

Input: cost = [10,15,20]

Output: 15

Explanation: You will start at index 1.
</br>- Pay 15 and climb two steps to reach the top.
</br>The total cost is 15.
## Example 2:

Input: cost = [1,100,1,1,1,100,1,1,100,1]

Output: 6

Explanation: You will start at index 0.
</br>- Pay 1 and climb two steps to reach index 2.
</br>- Pay 1 and climb two steps to reach index 4.
</br>- Pay 1 and climb two steps to reach index 6.
</br>- Pay 1 and climb one step to reach index 7.
</br>- Pay 1 and climb two steps to reach index 9.
</br>- Pay 1 and climb one step to reach the top.
</br>The total cost is 6.

Constraints:

- 2 <= cost.length <= 1000
- 0 <= cost[i] <= 999

# My solution (exceeds time limit, follows instructions)
```python
class Solution:
    def minCostClimbingStairs(self, cost: List[int]) -> int:
        # ==== 0. check input
		if not cost:
            return 0
			
        # ==== 1. create an array to memorize the results, and think about how you are going to
		# use/define it.
		# Here, I want this array to help me to memorize the "min cost" at the i-th step
        dp = [0] * len(cost)
        
		# ==== 2. Next, think about what are your first 3 cases (in most of cases) until you find the
		# pattern, which means "what do your dp[0], dp[1], dp[2]... look like?"
		# Let's start from dp[0]. My dp[0] would equal to cost[0] because I have no choice.
		dp[0] = cost[0]
		
		# My dp[1] would equal to cost[1]. I've wrote down "dp[1] = min(cost[0] + cost[1], cost[1])", 
		# but I found it is nonsense because in this problem, taking 2 costs will always higher than taking
		# 1 cost, which means cost[1] will always smaller than cost[0]+cost[1]. I mention this because I
		# want to let you know that you probably understand more about the relationships and the
		# problem itself when you are solving it.
        if len(cost) >= 2:
            dp[1] = cost[1]
        
		# Next, I try to write down my dp[2]. It was like:
		# dp[2] = cost[2] + min(dp[0], dp[1]) 
		# We found the pattern!!!!!!!!!!!!!
		# dp[i] would be "cost[i] + min(dp[i-2], dp[i-1])". The cost at the stairs plus the min of previous
		# one and two stairs (you could only come from the previous two stairs, and let's pick up the min
		# one.)
		
		# ==== 3. Once you found the pattern, use loop to help you!
		# We start from 2 because we already know the dp[0] and dp[1]. Also, the truth is: we are not
		# able to caculate dp[0] and dp[1]. However, from dp[2], we can caculate the results.
        for i in range(2, len(cost)):
            dp[i] = cost[i] + min(dp[i-1], dp[i-2])
        
		# ==== 4. Think again what you are trying to find in your dp array.
		# To finish the stairs journey in this problem, there are 2 ways to be the last step before we finish
		# the stairs. The last step might come from both last two stairs. So, we want to know the min of 
		# the costs of last 2 stairs from our dp array.
        return min(dp[-1], dp[-2])
```
