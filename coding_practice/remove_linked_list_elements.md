Location: https://leetcode.com/problems/remove-linked-list-elements/description/?envType=problem-list-v2&envId=linked-list
# Question
Given the head of a linked list and an integer val, remove all the nodes of the linked list that has Node.val == val, and return the new head.

# Example

## Example 1:

Input: head = [1,2,6,3,4,5,6], val = 6

Output: [1,2,3,4,5]

## Example 2:

Input: head = [], val = 1

Output: []

## Example 3:

Input: head = [7,7,7,7], val = 7

Output: []
 

## Constraints:

The number of nodes in the list is in the range [0, 104].\
1 <= Node.val <= 50\
0 <= val <= 50
 

# My solution (follows instructions on solutions)
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def removeElements(self, head, val):
        """
        :type head: Optional[ListNode]
        :type val: int
        :rtype: Optional[ListNode]
        """
        if head is None:
            return head
        new_node = ListNode(0)
        new_node.next = head
        current = new_node
        while current.next:
            if current.next.val == val:
                current.next = current.next.next
            else:
                current = current.next
        return new_node.next
```
