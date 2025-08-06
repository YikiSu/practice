Location: https://leetcode.com/problems/elimination-game/description/
# Question
You have a list arr of all integers in the range [1, n] sorted in a strictly increasing order. Apply the following algorithm on arr:

- Starting from left to right, remove the first number and every other number afterward until you reach the end of the list.
- Repeat the previous step again, but this time from right to left, remove the rightmost number and every other number from the remaining numbers.
- Keep repeating the steps again, alternating left to right and right to left, until a single number remains.

Given the integer n, return the last number that remains in arr.

 
# Example

## Example 1:

Input: n = 9

Output: 6

Explanation:\
arr = [1, 2, 3, 4, 5, 6, 7, 8, 9]\
arr = [2, 4, 6, 8]\
arr = [2, 6]\
arr = [6]

## Example 2:

Input: n = 1

Output: 1

## Constraints:

1 <= n <= 109
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def lastRemaining(self, n):
        """
        :type n: int
        :rtype: int
        """
        # def eliminate(arr):
        #     l = len(arr)
        #     curr = []
        #     for ind in range(1, l, 2):
        #         # print(arr[ind])
        #         curr.append(arr[ind])
        #     return curr[::-1]
        # ans = [num for num in range(1, n+1)]
        # while len(ans)>1:
        #     ans = eliminate(ans)
        # return ans[0]
        def helper(x, step, count, direction):
            if count < 2:
                return x
            increment = step if direction or count % 2 else 0
            return helper(x + increment, step * 2, count // 2, not direction)

        return helper(1, 1, n, True)
        
```
