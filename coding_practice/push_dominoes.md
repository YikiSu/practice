Location: https://leetcode.com/problems/push-dominoes/description/
# Question
There are n dominoes in a line, and we place each domino vertically upright. In the beginning, we simultaneously push some of the dominoes either to the left or to the right.

After each second, each domino that is falling to the left pushes the adjacent domino on the left. Similarly, the dominoes falling to the right push their adjacent dominoes standing on the right.

When a vertical domino has dominoes falling on it from both sides, it stays still due to the balance of the forces.

For the purposes of this question, we will consider that a falling domino expends no additional force to a falling or already fallen domino.

You are given a string dominoes representing the initial state where:

- dominoes[i] = 'L', if the ith domino has been pushed to the left,
- dominoes[i] = 'R', if the ith domino has been pushed to the right, and
- dominoes[i] = '.', if the ith domino has not been pushed.

Return a string representing the final state.

 
# Example

## Example 1:

Input: dominoes = "RR.L"

Output: "RR.L"

Explanation: The first domino expends no additional force on the second domino.

## Example 2:

Input: dominoes = ".L.R...LR..L.."

Output: "LL.RR.LLRRLL.."
## Constraints:

n == dominoes.length\
1 <= n <= 105\
dominoes[i] is either 'L', 'R', or '.'.
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def pushDominoes(self, dominoes):
        """
        :type dominoes: str
        :rtype: str
        """
        n = len(dominoes)
        right = [0]*n
        left = [0]*n
        ans = []
        for i in range(n):
            if dominoes[i] == "R":
                right[i] = n
            elif dominoes[i] == "." and i != 0 and right[i-1] > 0:
                right[i] = right[i-1]-1
        for i in range(n-1, -1, -1):
            if dominoes[i] == "L":
                left[i] = -n
            elif dominoes[i] == "." and i != n-1 and left[i+1]<0:
                left[i] = left[i+1]+1
        # print(right)
        # print(left)
        forces = [right[i]+left[i] for i in range(n)]
        ans = ""
        # print(forces)
        for i in range(n):
            if forces[i]>0:
                ans += "R"
            elif forces[i] < 0:
                ans += "L"
            else:
                ans += "."
        return ans
                
        # ans = ""
        # pre = ""
        # for i in range(len(dominoes)):
        #     # print(pre)
        #     # print(dominoes[i:])
        #     if dominoes[i] in ['L', 'R']:
        #         ans += dominoes[i]
        #     elif i != len(dominoes)-1:
        #         if pre == "R" and dominoes[i+1] == "L":
        #             ans += dominoes[i]
        #         elif pre == "R" and dominoes[i+1] == ".":
        #             # print('entering')
        #             ans += "R"
        #         elif dominoes[i+1] == "L":
        #             ans += "L"
        #         else:
        #             ans += dominoes[i]
        #     else:
        #         if pre == "R":
        #             ans += "R"
        #         else:
        #             ans += dominoes[i]
        #     pre = dominoes[i]
        #     # print(ans)
        # return ans
            
```
