Location: https://leetcode.com/problems/longest-zigzag-path-in-a-binary-tree/description/?envType=study-plan-v2&envId=leetcode-75
# Question

You are given the root of a binary tree.

A ZigZag path for a binary tree is defined as follow:

- Choose any node in the binary tree and a direction (right or left).
- If the current direction is right, move to the right child of the current node; otherwise, move to the left child.
- Change the direction from right to left or from left to right.
- Repeat the second and third steps until you can't move in the tree.
</br>Zigzag length is defined as the number of nodes visited - 1. (A single node has a length of 0).

Return the longest ZigZag path contained in that tree.

# Example

## Example 1:

Input: root = [1,null,1,1,1,null,null,1,1,null,1,null,null,null,1]

Output: 3

**Explanation**: Longest ZigZag path in blue nodes (right -> left -> right).

## Example 2:

Input:  root = [1,1,1,null,1,null,null,1,1,null,1]

Output: 4

**Explanation**: Longest ZigZag path in blue nodes (left -> right -> left -> right).

## Example 3:

Input:  root = [1]

Output: 0

**Explanation**: Root is considered as good.

Constraints:

- The number of nodes in the tree is in the range [1, 5 * 104].
- 1 <= Node.val <= 100

# My solution (followed solutions of others)
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def longestZigZag(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: int
        """
        max_ = [0]
        pre = None
        def checks_(root, pre, cursum):
            if not root:
                return
            if pre == "right":
                if root.left:
                    cursum += 1
                    max_[0] = max(cursum, max_[0])
                    checks_(root.left, "left", cursum)
                checks_(root.right, "right", 1)
            elif pre == "left":
                if root.right:
                    cursum += 1
                    max_[0] = max(cursum, max_[0])
                    checks_(root.right, "right", cursum)
                checks_(root.left, "left", 1)
            else:
                if root.left or root.right:
                    max_[0] = max(1, max_[0])
                checks_(root.left, "left", 1)
                checks_(root.right, "right", 1)
        checks_(root, pre, max_[0])
        return max_[0]


```
