Location: https://leetcode.com/problems/reverse-linked-list/description/?envType=study-plan-v2&envId=leetcode-75
# Question
You are given the head of a linked list. Delete the middle node, and return the head of the modified linked list.

The middle node of a linked list of size n is the ⌊n / 2⌋th node from the start using 0-based indexing, where ⌊x⌋ denotes the largest integer less than or equal to x.

For n = 1, 2, 3, 4, and 5, the middle nodes are 0, 1, 1, 2, and 2, respectively.
 
 
# Example

## Example 1:

Input: head = [1,2,3,4,5]

Output: [5,4,3,2,1]

## Example 2:

Input:  head = [1,2]

Output: [2,1]

## Example 3:

Input: head = []

Output: []
  

Constraints:

- The number of nodes in the list is the range [0, 5000].
- -5000 <= Node.val <= 5000
 

# My solution (followed solutions of others: https://leetcode.com/problems/reverse-linked-list/solutions/58338/python-solution-simple-iterative/?envType=study-plan-v2&envId=leetcode-75)
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reverseList(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        pre = None
        curr = head
        while curr:
            next = curr.next
            curr.next = pre
            pre = curr
            curr = next
        return pre
        
```
