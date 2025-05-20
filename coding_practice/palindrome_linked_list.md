Location: https://leetcode.com/problems/palindrome-linked-list/description/?envType=problem-list-v2&envId=linked-list
# Question
Given the head of a singly linked list, return true if it is a palindrome or false otherwise.

 
# Example

## Example 1:

Input: head = [1,2,2,1]

Output: true

## Example 2:

Input: head = [1,2]

Output: false
 

## Constraints:

The number of nodes in the list is in the range [1, 105].\
0 <= Node.val <= 9
 

# My solution (follows instructions on solutions)
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def isPalindrome(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: bool
        """
        if head is None or head.next is None:
            return True
        # stack = []
        # while head:
        #     curr = head.val
        #     head = head.next
        #     if stack and curr == stack[-1]:
        #         stack.pop(-1)
        #     else:
        #         stack.append(curr)
        # return len(stack) == 0
        slow = fast = head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
        # With slow now at the middle, we can reverse the back half of the list with the help of another variable to
        # contain a reference to the previous node (prev) and a three-way swap.
        # Before we do this, however, we'll want to set prev.next = null, so that we break the reverse cycle and avoid an endless loop.
        pre = None
        curr = slow
        while curr:
            next_node = curr.next
            curr.next = pre
            pre = curr
            curr = next_node
        first, second = head, pre
        while second:
            if first.val != second.val:
                return False
            first = first.next
            second = second.next
        return True
```
