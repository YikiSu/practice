Location: https://leetcode.com/problems/leaf-similar-trees/description/?envType=study-plan-v2&envId=leetcode-75
# Question
Consider all the leaves of a binary tree, from left to right order, the values of those leaves form a leaf value sequence.

For example, in the given tree above, the leaf value sequence is (6, 7, 4, 9, 8).

Two binary trees are considered leaf-similar if their leaf value sequence is the same.

Return true if and only if the two given trees with head nodes root1 and root2 are leaf-similar.

# Example

## Example 1:

Input: root1 = [3,5,1,6,2,9,8,null,null,7,4], root2 = [3,5,1,6,7,4,2,null,null,null,null,null,null,9,8]

Output: true


## Example 2:

Input: root1 = [1,2,3], root2 = [1,3,2]

Output: false


Constraints:

- The number of nodes in each tree will be in the range [1, 200].
- Both of the given trees will have values in the range [0, 200].
 

# My solution (follows instructions on solutions)
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def leafSimilar(self, root1, root2):
        """
        :type root1: Optional[TreeNode]
        :type root2: Optional[TreeNode]
        :rtype: bool
        """
        def end_of_leave(tree):
            if not tree:
                return []
            leaves = end_of_leave(tree.left) + end_of_leave(tree.right)
            return leaves or [tree.val]
        ans1 = end_of_leave(root1)
        ans2 = end_of_leave(root2)
        return ans1 == ans2


```
