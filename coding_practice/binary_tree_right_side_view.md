Location: https://leetcode.com/problems/binary-tree-right-side-view/description/?envType=study-plan-v2&envId=leetcode-75
# Question

Given the root of a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.

# Example

## Example 1:

Input: root = [1,2,3,null,5,null,4]

Output: [1,3,4]


## Example 2:

Input:  root = [1,2,3,4,null,null,null,5]

Output:  [1,3,4,5]

## Example 3:

Input:  root = [1,null,3]

Output: [1,3]

## Example 4:

Input:  root = []

Output: []

Constraints:

- The number of nodes in the tree is in the range [0, 100].
- -100 <= Node.val <= 100

# My solution (followed solutions of others)
```python
import collections
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def rightSideView(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: List[int]
        """
        if not root:
            return []
        res = []
        queue = collections.deque()
        queue.append(root)
        while queue:
            level_len = len(queue)
            for i in range(level_len):
                node = queue.popleft()
                if i == level_len-1:
                    res.append(node.val)
                if node.left:
                    queue.append(node.left)
                if node.right:
                    queue.append(node.right)
        return res

```
