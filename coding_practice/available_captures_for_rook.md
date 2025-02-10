Location: https://leetcode.com/problems/available-captures-for-rook/description/
# Question
You are given an 8 x 8 matrix representing a chessboard. There is exactly one white rook represented by 'R', some number of white bishops 'B', and some number of black pawns 'p'. Empty squares are represented by '.'.

A rook can move any number of squares horizontally or vertically (up, down, left, right) until it reaches another piece or the edge of the board. A rook is attacking a pawn if it can move to the pawn's square in one move.

Note: A rook cannot move through other pieces, such as bishops or pawns. This means a rook cannot attack a pawn if there is another piece blocking the path.

Return the number of pawns the white rook is attacking.

 
# Example

## Example 1:

Input: board = [[".",".",".",".",".",".",".","."],[".",".",".","p",".",".",".","."],[".",".",".","R",".",".",".","p"],[".",".",".",".",".",".",".","."],[".",".",".",".",".",".",".","."],[".",".",".","p",".",".",".","."],[".",".",".",".",".",".",".","."],[".",".",".",".",".",".",".","."]]

Output: 3

Explanation:

In this example, the rook is attacking all the pawns.

## Example 2:

Input: board = [[".",".",".",".",".",".","."],[".","p","p","p","p","p",".","."],[".","p","p","B","p","p",".","."],[".","p","B","R","B","p",".","."],[".","p","p","B","p","p",".","."],[".","p","p","p","p","p",".","."],[".",".",".",".",".",".",".","."],[".",".",".",".",".",".",".","."]]

Output: 0

Explanation:

The bishops are blocking the rook from attacking any of the pawns.

## Example 3:

Input: board = [[".",".",".",".",".",".",".","."],[".",".",".","p",".",".",".","."],[".",".",".","p",".",".",".","."],["p","p",".","R",".","p","B","."],[".",".",".",".",".",".",".","."],[".",".",".","B",".",".",".","."],[".",".",".","p",".",".",".","."],[".",".",".",".",".",".",".","."]]

Output: 3

Explanation:

The rook is attacking the pawns at positions b5, d6, and f5.
 

Constraints:

board.length == 8\
board[i].length == 8\
board[i][j] is either 'R', '.', 'B', or 'p'\
There is exactly one cell with board[i][j] == 'R'
 

# My solution (follows instructions on solutions)
```python
import collections
class Solution(object):
    def numRookCaptures(self, board):
        """
        :type board: List[List[str]]
        :rtype: int
        """
        for i in range(len(board)):
            for j in range(len(board[0])):
                if board[i][j] == "R":
                    rook = [i, j]
        directions = [[-1,0], [0,-1],[1,0],[0,1]]
        ans = 0
        for d in directions:
            row = rook[0]
            col = rook[1]
            if d[0] < 0:
                row -= 1
                while row >= 0:
                    if board[row][col] == 'p':
                        ans += 1
                        break
                    elif board[row][col] == 'B':
                        break
                    else:
                        row -= 1
            elif d[0] > 0 :
                row += 1
                while row < len(board):
                    if board[row][col] == 'p':
                        ans += 1
                        break
                    elif board[row][col] == 'B':
                        break
                    else:
                        row += 1
            elif d[1] > 0 :
                col += 1
                while col < len(board):
                    if board[row][col] == 'p':
                        ans += 1
                        break
                    elif board[row][col] == 'B':
                        break
                    else:
                        col += 1
            else:
                col -= 1
                while col >= 0:
                    if board[row][col] == 'p':
                        ans += 1
                        break
                    elif board[row][col] == 'B':
                        break
                    else:
                        col -= 1
        return ans

        
```
