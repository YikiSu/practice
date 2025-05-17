Location: https://leetcode.com/problems/remove-duplicates-from-sorted-list/description/?envType=problem-list-v2&envId=linked-list
# Question
Given the head of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.

 
# Example

## Example 1:

Input: head = [1,1,2]

Output: [1,2]

## Example 2:

Input: head = [1,1,2,3,3]

Output: [1,2,3]

## Constraints:

The number of nodes in the list is in the range [0, 300].\
-100 <= Node.val <= 100\
The list is guaranteed to be sorted in ascending order.
 

# My solution (follows instructions on solutions)
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def deleteDuplicates(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        current = head
        while current and current.next:
            if current.next.val == current.val:
                current.next = current.next.next
            else:
                current = current.next
        return head
```
