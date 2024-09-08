Location: [https://leetcode.com/problems/climbing-stairs/description/]
# Question
You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

# Example

## Example 1:

Input: n = 2

Output: 2

Explanation: There are two ways to climb to the top.

1. 1 step + 1 step

2. 2 steps

## Example 2:

Input: n = 3

Output: 3

Explanation: There are three ways to climb to the top.

1. 1 step + 1 step + 1 step

2. 1 step + 2 steps

3. 2 steps + 1 step
 

Constraints:

1 <= n <= 45
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        a, b = 1, 2
        for i in range(n-1):
            a, b = b, a+b
        return a
```
## Explaination
**Fibonacci pattern**

The relationship follows the Fibonacci pattern because it only can move either 1 or 2 steps at a time.

How fibonacci intution works here?

Base Cases:

1 Step: 1 way (1 step).
<br>2 Steps: 2 ways (two 1-steps or one 2-step).

Recurrence Relation for Step k (where k > 2):

<br>Reach from k-1 with 1 step.
<br>Reach from k-2 with 2 steps.
<br>Ways to reach k = Ways to k-1 + Ways to k-2.

Example:

<br>n = 1, Step: 1 way.
<br>n = 2, Steps: 2 ways.
<br>n = 3, Steps: 1 + 2 = 3 ways.
<br>n = 4, Steps: 2 + 3 = 5 ways.
<br>n = 5, Steps: 3 + 5 = 8 ways.
<br>This sequence of ways to climb (1, 2, 3, 5, 8) follows the Fibonacci pattern, where each number is the sum of the two preceding ones.
