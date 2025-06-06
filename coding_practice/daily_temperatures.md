Location: https://leetcode.com/problems/daily-temperatures/description/?envType=problem-list-v2&envId=monotonic-stack
# Question
Given an array of integers temperatures represents the daily temperatures, return an array answer such that answer[i] is the number of days you have to wait after the ith day to get a warmer temperature. If there is no future day for which this is possible, keep answer[i] == 0 instead.

 
# Example

## Example 1:

Input: temperatures = [73,74,75,71,69,72,76,73]

Output: [1,1,4,2,1,1,0,0]
## Example 2:

Input: temperatures = [30,40,50,60]

Output: [1,1,1,0]

## Example 3:

Input: temperatures = [30,60,90]

Output: [1,1,0]
 

## Constraints:

1 <= temperatures.length <= 105\
30 <= temperatures[i] <= 100
 

# My solution 
```python
class Solution(object):
    def dailyTemperatures(self, temperatures):
        """
        :type temperatures: List[int]
        :rtype: List[int]
        """
        stack = []
        ans = [0] * len(temperatures)
        for ind, temp in enumerate(temperatures):
            # print(stack)
            while stack and temp > temperatures[stack[-1]]:
                curr = stack.pop()
                ans[curr] = ind-curr
            stack.append(ind)
            # print(stack)        
        return ans
```
