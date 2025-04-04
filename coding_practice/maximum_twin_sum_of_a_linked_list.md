
Location: https://leetcode.com/problems/maximum-twin-sum-of-a-linked-list/description/?envType=study-plan-v2&envId=leetcode-75
# Question
In a linked list of size n, where n is even, the ith node (0-indexed) of the linked list is known as the twin of the (n-1-i)th node, if 0 <= i <= (n / 2) - 1.

- For example, if n = 4, then node 0 is the twin of node 3, and node 1 is the twin of node 2. These are the only nodes with twins for n = 4.
The twin sum is defined as the sum of a node and its twin.

Given the head of a linked list with even length, return the maximum twin sum of the linked list.

# Example

## Example 1:

Input: head = [5,4,2,1]

Output: 6

Explanation: Nodes 0 and 1 are the twins of nodes 3 and 2, respectively. All have twin sum = 6.
</br>There are no other nodes with twins in the linked list.
</br>Thus, the maximum twin sum of the linked list is 6. 

## Example 2:

Input:  head = [4,2,2,3]

Output: 7

Explanation: The nodes with twins present in this linked list are:
- Node 0 is the twin of node 3 having a twin sum of 4 + 3 = 7.
- Node 1 is the twin of node 2 having a twin sum of 2 + 2 = 4.
</br>Thus, the maximum twin sum of the linked list is max(7, 4) = 7. 

## Example 3:

Input:  head = [1,100000]

Output: 100001

Explanation: There is only one node with a twin in the linked list having twin sum of 1 + 100000 = 100
  

Constraints:

- The number of nodes in the list is an even integer in the range [2, 105].
- 1 <= Node.val <= 105
 

# My solution 
```python
class Solution(object):
    def pairSum(self, head):
        """
        :type head: Optional[ListNode]
        :rtype: int
        """
        ind1 = []
        ans = 0
        while head != None and head.next != None:
            ind1.append(head.val)
            head = head.next
        ind1.append(head.val)
        for i in range(len(ind1)/2):
            ans = max(ans, ind1[i]+ind1[len(ind1)-1-i])
        return ans

        
```
