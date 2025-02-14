Location: https://leetcode.com/problems/same-tree/description/?envType=problem-list-v2&envId=breadth-first-search
# Question
Given the roots of two binary trees p and q, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.
 
# Example

## Example 1:

Input: p = [1,2,3], q = [1,2,3]

Output: true

## Example 2:

Input: p = [1,2], q = [1,null,2]

Output: false

## Example 3:

Input: p = [1,2,1], q = [1,1,2]

Output: false
 

Constraints:

The number of nodes in both trees is in the range [0, 100].\
-104 <= Node.val <= 104
 

# My solution 
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isSameTree(self, p, q):
        """
        :type p: Optional[TreeNode]
        :type q: Optional[TreeNode]
        :rtype: bool
        """
        if not p and q:
            return False
        if not q and p:
            return False
        if not p and not q:
            return True
        pq = deque([p])
        qq = deque([q])
        while pq and qq:
            pcurr = pq.popleft()
            qcurr = qq.popleft()
            if pcurr.val != qcurr.val:
                return False
            if pcurr.left and qcurr.left:
                pq.append(pcurr.left)
                qq.append(qcurr.left)
            elif (pcurr.left and not qcurr.left) or (not pcurr.left and qcurr.left):
                return False
            if pcurr.right and qcurr.right:
                pq.append(pcurr.right)
                qq.append(qcurr.right)
            elif (pcurr.right and not qcurr.right) or (not pcurr.right and qcurr.right):
                return False
        if (pq and not qq) or (not pq and qq):
            return False
        else:
            return True

```
