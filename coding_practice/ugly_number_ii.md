Location: https://leetcode.com/problems/ugly-number-ii/description/?envType=problem-list-v2&envId=heap-priority-queue
# Question
An ugly number is a positive integer whose prime factors are limited to 2, 3, and 5.

Given an integer n, return the nth ugly number.
 
# Example

## Example 1:

Input: n = 10

Output: 12

Explanation: [1, 2, 3, 4, 5, 6, 8, 9, 10, 12] is the sequence of the first 10 ugly numbers.

## Example 2:

Input: n = 1

Output: 1

Explanation: 1 has no prime factors, therefore all of its prime factors are limited to 2, 3, and 5.

Constraints:

1 <= n <= 1690 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def nthUglyNumber(self, n):
        """
        :type n: int
        :rtype: int
        """
        ugly = [1]
        p2, p3, p5 = 0, 0, 0
        for i in range(n-1):
            next_ugly = min(ugly[p2]*2, ugly[p3]*3, ugly[p5]*5)
            ugly.append(next_ugly)

            if next_ugly == ugly[p2]*2:
                p2 += 1
            if next_ugly == ugly[p3]*3:
                p3 += 1
            if next_ugly == ugly[p5]*5:
                p5 += 1
        return ugly[-1]
        
```
