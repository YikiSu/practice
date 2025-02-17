Location: https://leetcode.com/problems/symmetric-tree/description/?envType=problem-list-v2&envId=breadth-first-search
# Question
Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).
 
# Example

## Example 1:

Input: root = [1,2,2,3,4,4,3]

Output: true

## Example 2:

Input: root = [1,2,2,null,3,null,3]
Output: false

Constraints:

The number of nodes in the tree is in the range [1, 1000].\
-100 <= Node.val <= 100
 

# My solution (follows instructions on solutions)
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isSymmetric(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: bool
        """
        if not root:
            return True
        q = deque([(root.left, root.right)])
        while q:
            l, r = q.popleft()
            if not l and not r:
                continue
            if not l or not r or l.val != r.val:
                return False
            q.append([l.left, r.right])
            q.append([l.right, r.left])
        return True

        
```
