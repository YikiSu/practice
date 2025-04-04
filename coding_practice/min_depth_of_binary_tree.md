Location: https://leetcode.com/problems/minimum-depth-of-binary-tree/description/?envType=problem-list-v2&envId=breadth-first-search
# Question
Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

Note: A leaf is a node with no children.
 
# Example

## Example 1:

Input: root = [3,9,20,null,null,15,7]

Output: 2

## Example 2:

Input: root = [2,null,3,null,4,null,5,null,6]

Output: 5

Constraints:

The number of nodes in the tree is in the range [0, 105].\
1000 <= Node.val <= 1000
 

# My solution 
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def minDepth(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: int
        """
        if not root:
            return 0
        q = deque([root])
        level = 0
        while q:
            size = len(q)
            cur_level = []
            for _ in range(size):
                node = q.popleft()
                cur_level.append(node)
                if not node.left and not node.right:
                    return level + 1
                if node.left:
                    q.append(node.left)
                if node.right:
                    q.append(node.right)
            level += 1
        return level
```
