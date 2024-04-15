Location: https://leetcode.com/problems/invert-binary-tree/description/

# Question
Given the root of a binary tree, invert the tree, and return its root.

# Solution (don't know how to do it, follow instructions)
```python
class Solution(object):
    def invertTree(self, root):
        """
        :type root: TreeNode
        :rtype: TreeNode
        """
        if not root:
            return root
        self.invertTree(root.left)
        self.invertTree(root.right)
        root.left, root.right = root.right, root.left
        return root
```
