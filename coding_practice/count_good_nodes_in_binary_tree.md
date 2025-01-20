Location: https://leetcode.com/problems/count-good-nodes-in-binary-tree/description/?envType=study-plan-v2&envId=leetcode-75
# Question

Given a binary tree root, a node X in the tree is named good if in the path from root to X there are no nodes with a value greater than X.

Return the number of good nodes in the binary tree.

# Example

## Example 1:

Input: root = [3,1,4,3,null,1,5]

Output: 4

**Explanation**: Nodes in blue are good.
</br>Root Node (3) is always a good node.
</br>Node 4 -> (3,4) is the maximum value in the path starting from the root.
</br>Node 5 -> (3,4,5) is the maximum value in the path
</br>Node 3 -> (3,1,3) is the maximum value in the path.

## Example 2:

Input:  root = [3,3,null,4,2]

Output: 3

**Explanation**: Nodes in blue are good.
</br>Node 2 -> (3, 3, 2) is not good, because "3" is higher than it.

## Example 3:

Input:  root = [1]

Output: 1

**Explanation**: Root is considered as good.

Constraints:

- The number of nodes in the binary tree is in the range [1, 10^5].
- Each node's value is between [-10^4, 10^4].

# My solution (followed solutions of others)
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def goodNodes(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        if not root:
            return 0
        cnt = [0]
        def check_nodes(root, max_):
            if not root:
                return 
            if root.val >= max_:
                cnt[0] += 1
                max_ = root.val
            check_nodes(root.left, max_) 
            check_nodes(root.right, max_)
        
        check_nodes(root, root.val)
        return cnt[0]

```
