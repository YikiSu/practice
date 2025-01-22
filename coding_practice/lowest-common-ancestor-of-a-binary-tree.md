Location: https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/?envType=study-plan-v2&envId=leetcode-75
# Question

Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants (where we allow a node to be a descendant of itself).”

# Example

## Example 1:

Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1

Output: 3

**Explanation**: The LCA of nodes 5 and 1 is 3.

## Example 2:

Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4

Output: 5

**Explanation**: The LCA of nodes 5 and 4 is 5, since a node can be a descendant of itself according to the LCA definition.

## Example 3:

Input: root = [1,2], p = 1, q = 2

Output: 1

Constraints:

- The number of nodes in the tree is in the range [2, 105].
- -109 <= Node.val <= 109
- All Node.val are unique.
- p != q
- p and q will exist in the tree.

# My solution (followed solutions of others)
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def lowestCommonAncestor(self, root, p, q):
        """
        :type root: TreeNode
        :type p: TreeNode
        :type q: TreeNode
        :rtype: TreeNode
        """
        if not root or root == p or root == q:
            return root
        l = self.lowestCommonAncestor(root.left, p, q)
        r = self.lowestCommonAncestor(root.right, p, q)
        if l and r:
            return root
        return l or r
```

## Explanations?
1. search left-right until p or q is found, say it was p.
2. when p is found, then go to the opposite side of a tree searching for q, do not try to search down the found p (!)
3. if there is no q on the opposite side, then just return found p as it is an anwser; q is somewhere in the children nodes of p that's why we didn't search down the p
4. if there is q on the opposite side, then go up the recursion stack until both left and right nodes are not None which means it is their LWA.
