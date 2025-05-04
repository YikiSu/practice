Location: https://leetcode.com/problems/spiral-matrix-iv/description/
# Question
You are given two integers m and n, which represent the dimensions of a matrix.

You are also given the head of a linked list of integers.

Generate an m x n matrix that contains the integers in the linked list presented in spiral order (clockwise), starting from the top-left of the matrix. If there are remaining empty spaces, fill them with -1.

Return the generated matrix.

 
# Example

## Example 1:

Input: m = 3, n = 5, head = [3,0,2,6,8,1,7,9,4,2,5,5,0]

Output: [[3,0,2,6,8],[5,0,-1,-1,1],[5,2,4,9,7]]

Explanation: The diagram above shows how the values are printed in the matrix.\
Note that the remaining spaces in the matrix are filled with -1.

## Example 2:

Input: m = 1, n = 4, head = [0,1,2]

Output: [[0,1,2,-1]]

Explanation: The diagram above shows how the values are printed from left to right in the matrix.\
The last space in the matrix is set to -1.

## Constraints:

1 <= m, n <= 105\
1 <= m * n <= 105\
The number of nodes in the list is in the range [1, m * n].\
0 <= Node.val <= 1000
 

# My solution (follows instructions on solutions)
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def spiralMatrix(self, m, n, head):
        """
        :type m: int
        :type n: int
        :type head: Optional[ListNode]
        :rtype: List[List[int]]
        """
        ans = [[-1]*n for _ in range(m)]
        direction = (1, 1)
        seen = set()
        r, c = 0, 0
        while head:
            curr = head.val
            head = head.next
            # print(r)
            # print(c)
            # print(curr)
            ans[r][c] = curr
            seen.add((r,c))
            if direction[0]>0 and direction[1]> 0:
                c += 1
                if (r,c) in seen or c==n:
                    r += 1
                    c -= 1
                    direction = (1,-1)
            elif direction[0]>0 and direction[1]<0:
                r += 1
                if (r,c) in seen or r==m:
                    r -= 1
                    c -= 1
                    direction = (-1, -1)
            elif direction[0]<0 and direction[1]<0:
                c -= 1
                if (r,c) in seen or c < 0:
                    c += 1
                    r -= 1
                    direction = (-1, 1)
            else:
                r -= 1
                if (r,c) in seen or r < 0:
                    r += 1
                    c += 1
                    direction = (1,1)
        return ans

```
