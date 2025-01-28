Location: https://leetcode.com/problems/nearest-exit-from-entrance-in-maze/description/?envType=study-plan-v2&envId=leetcode-75
# Question
You are given an m x n matrix maze (0-indexed) with empty cells (represented as '.') and walls (represented as '+'). You are also given the entrance of the maze, where entrance = [entrancerow, entrancecol] denotes the row and column of the cell you are initially standing at.

In one step, you can move one cell up, down, left, or right. You cannot step into a cell with a wall, and you cannot step outside the maze. Your goal is to find the nearest exit from the entrance. An exit is defined as an empty cell that is at the border of the maze. The entrance does not count as an exit.

Return the number of steps in the shortest path from the entrance to the nearest exit, or -1 if no such path exists.

 
# Example

## Example 1:

Input: maze = [["+","+",".","+"],[".",".",".","+"],["+","+","+","."]], entrance = [1,2]

Output: 1

Explanation: There are 3 exits in this maze at [1,0], [0,2], and [2,3].
</br>Initially, you are at the entrance cell [1,2].
</br>- You can reach [1,0] by moving 2 steps left.
</br>- You can reach [0,2] by moving 1 step up.
</br>It is impossible to reach [2,3] from the entrance.
</br>Thus, the nearest exit is [0,2], which is 1 step away.

## Example 2:

Input: maze = [["+","+","+"],[".",".","."],["+","+","+"]], entrance = [1,0]

Output: 2

Explanation: There is 1 exit in this maze at [1,2].
</br>[1,0] does not count as an exit since it is the entrance cell.
</br>Initially, you are at the entrance cell [1,0].
</br>- You can reach [1,2] by moving 2 steps right.
</br>Thus, the nearest exit is [1,2], which is 2 steps away.
 
## Example 2:

Input: maze = [[".","+"]], entrance = [0,0]

Output: -1

Explanation: There are no exits in this maze.

Constraints:

- maze.length == m
- maze[i].length == n
- 1 <= m, n <= 100
- maze[i][j] is either '.' or '+'.
- entrance.length == 2
- 0 <= entrancerow < m
- 0 <= entrancecol < n
- entrance will always be an empty cell.
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def nearestExit(self, maze, entrance):
        """
        :type maze: List[List[str]]
        :type entrance: List[int]
        :rtype: int
        """
        dirs = [(0,1),(0,-1),(1,0),(-1,0)]
        entrance = (entrance[0],entrance[1])
        q = deque([entrance])
        visited = set()
        visited.add(entrance)
        step = 0
        while q:
            stepLength = len(q)
            for i in range(stepLength): # here, we can use length of the deque to iterate through level by level
                node = q.popleft()
                if node[0] == 0 or node[0] == len(maze) -1 or node[1] == 0 or node[1] == len(maze[0]) -1 :
                    if maze[node[0]][node[1]] == '.' and (node[0],node[1]) != entrance:
                        return step
                for d in dirs:
                    newD = (node[0] + d[0], node[1] + d[1])
                    if newD not in visited and 0<=newD[0]<len(maze) and 0<=newD[1]<len(maze[0]) and maze[newD[0]][newD[1]] == '.': # only add valid nodes to the queue!
                        visited.add(newD) # mark it as visited, so we don't loop forever
                        q.append(newD)
            step += 1 # after we finish with a level, increment step by one
        return -1
```
