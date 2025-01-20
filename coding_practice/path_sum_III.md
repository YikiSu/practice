Location: https://leetcode.com/problems/path-sum-iii/description/?envType=study-plan-v2&envId=leetcode-75
# Question

Given the root of a binary tree and an integer targetSum, return the number of paths where the sum of the values along the path equals targetSum.

The path does not need to start or end at the root or a leaf, but it must go downwards (i.e., traveling only from parent nodes to child nodes).

# Example

## Example 1:

Input: root = [10,5,-3,3,2,null,11,3,-2,null,1], targetSum = 8

Output: 3

**Explanation**: The paths that sum to 8 are shown.

## Example 2:

Input: root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22

Output: 3


Constraints:

- The number of nodes in the tree is in the range [0, 1000].
- -109 <= Node.val <= 109
- -1000 <= targetSum <= 1000

# My solution (followed solutions of others)
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def pathSum(self, root, targetSum):
        """
        :type root: Optional[TreeNode]
        :type targetSum: int
        :rtype: int
        """
        cnt = [0]
        def dfs(node, cursum):
            if not node:
                return
            if cursum + node.val == targetSum:
                cnt[0] += 1
            dfs(node.left, cursum + node.val)
            dfs(node.right, cursum + node.val)

        def dfs_starter(node):
            if not node:
                return
            dfs(node, 0)
            dfs_starter(node.left)
            dfs_starter(node.right)

        dfs_starter(root)
        return cnt[0]

```
