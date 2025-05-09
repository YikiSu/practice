Location: https://leetcode.com/problems/add-two-numbers/description/
# Question
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.
 
# Example

## Example 1:

Input: l1 = [2,4,3], l2 = [5,6,4]

Output: [7,0,8]

Explanation: 342 + 465 = 807.

## Example 2:

Input: l1 = [0], l2 = [0]

Output: [0]

## Example 3:

Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]

Output: [8,9,9,9,0,0,0,1]
 

## Constraints:

The number of nodes in each linked list is in the range [1, 100].\
0 <= Node.val <= 9\
It is guaranteed that the list represents a number that does not have leading zeros.
 

# My solution (follows instructions on solutions)
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: Optional[ListNode]
        :type l2: Optional[ListNode]
        :rtype: Optional[ListNode]
        """
        pre = 0
        ans = ListNode(0)
        tail = ans
        while l1 or l2 or pre != 0:
            curr = 0
            if l1:
                curr += l1.val
                l1 = l1.next
            if l2:
                curr += l2.val
                l2 = l2.next
            curr += pre
            digit = curr%10
            pre = curr//10

            new = ListNode(digit)
            tail.next = new
            tail = tail.next
        res = ans.next
        ans.next = None
        return res

```
