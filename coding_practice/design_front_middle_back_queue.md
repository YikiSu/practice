Location: https://leetcode.com/problems/design-front-middle-back-queue/description/
# Question
Design a queue that supports push and pop operations in the front, middle, and back.

Implement the FrontMiddleBack class:

- FrontMiddleBack() Initializes the queue.
- void pushFront(int val) Adds val to the front of the queue.
- void pushMiddle(int val) Adds val to the middle of the queue.
- void pushBack(int val) Adds val to the back of the queue.
- int popFront() Removes the front element of the queue and returns it. If the queue is empty, return -1.
- int popMiddle() Removes the middle element of the queue and returns it. If the queue is empty, return -1.
- int popBack() Removes the back element of the queue and returns it. If the queue is empty, return -1.

Notice that when there are two middle position choices, the operation is performed on the frontmost middle position choice. For example:

- Pushing 6 into the middle of [1, 2, 3, 4, 5] results in [1, 2, 6, 3, 4, 5].
- Popping the middle from [1, 2, 3, 4, 5, 6] returns 3 and results in [1, 2, 4, 5, 6].
 
# Example

## Example 1:

Input:\
["FrontMiddleBackQueue", "pushFront", "pushBack", "pushMiddle", "pushMiddle", "popFront", "popMiddle", "popMiddle", "popBack", "popFront"]\
[[], [1], [2], [3], [4], [], [], [], [], []]

Output:\
[null, null, null, null, null, 1, 3, 4, 2, -1]

Explanation:\
FrontMiddleBackQueue q = new FrontMiddleBackQueue();\
q.pushFront(1);   // [1]\
q.pushBack(2);    // [1, 2]\
q.pushMiddle(3);  // [1, 3, 2]\
q.pushMiddle(4);  // [1, 4, 3, 2]\
q.popFront();     // return 1 -> [4, 3, 2]\
q.popMiddle();    // return 3 -> [4, 2]\
q.popMiddle();    // return 4 -> [2]\
q.popBack();      // return 2 -> []\
q.popFront();     // return -1 -> [] (The queue is empty)

## Constraints:

1 <= val <= 109\
At most 1000 calls will be made to pushFront, pushMiddle, pushBack, popFront, popMiddle, and popBack.
 

# My solution 
```python
class FrontMiddleBackQueue(object):

    def __init__(self):
        self.stack = []

    def pushFront(self, val):
        """
        :type val: int
        :rtype: None
        """
        self.stack = [val]+self.stack
        

    def pushMiddle(self, val):
        """
        :type val: int
        :rtype: None
        """
        if not self.stack:
            self.stack.append(val)
        else:
            middle = len(self.stack)//2
            self.stack = self.stack[:middle]+[val]+self.stack[middle:]
        # print(self.stack)

    def pushBack(self, val):
        """
        :type val: int
        :rtype: None
        """
        self.stack.append(val)
        

    def popFront(self):
        """
        :rtype: int
        """
        if not self.stack:
            return -1
        else:
            return self.stack.pop(0)
        

    def popMiddle(self):
        """
        :rtype: int
        """
        if not self.stack:
            return -1
        else:
            if len(self.stack)%2 != 0:
                middle = len(self.stack)//2
            else:
                middle = len(self.stack)//2-1
            middle_val = self.stack[middle]
            self.stack = self.stack[:middle]+self.stack[middle+1:]
            return middle_val
        

    def popBack(self):
        """
        :rtype: int
        """
        if not self.stack:
            return -1
        else:
            return self.stack.pop(-1)
        


# Your FrontMiddleBackQueue object will be instantiated and called as such:
# obj = FrontMiddleBackQueue()
# obj.pushFront(val)
# obj.pushMiddle(val)
# obj.pushBack(val)
# param_4 = obj.popFront()
# param_5 = obj.popMiddle()
# param_6 = obj.popBack()
```
