Location: https://leetcode.com/problems/snapshot-array/description/
# Question
Implement a SnapshotArray that supports the following interface:

- SnapshotArray(int length) initializes an array-like data structure with the given length. Initially, each element equals 0.
- void set(index, val) sets the element at the given index to be equal to val.
- int snap() takes a snapshot of the array and returns the snap_id: the total number of times we called snap() minus 1.
- int get(index, snap_id) returns the value at the given index, at the time we took the snapshot with the given snap_id
 
# Example

## Example 1:

Input: ["SnapshotArray","set","snap","set","get"]\
[[3],[0,5],[],[0,6],[0,0]]

Output: [null,null,0,null,5]

Explanation: \
SnapshotArray snapshotArr = new SnapshotArray(3); // set the length to be 3\
snapshotArr.set(0,5);  // Set array[0] = 5\
snapshotArr.snap();  // Take a snapshot, return snap_id = 0\
snapshotArr.set(0,6);\
snapshotArr.get(0,0);  // Get the value of array[0] with snap_id = 0, return 5

## Constraints:

1 <= length <= 5 * 104\
0 <= index < length\
0 <= val <= 109\
0 <= snap_id < (the total number of times we call snap())\
At most 5 * 104 calls will be made to set, snap, and get.
 

# My solution (follows instructions on solutions)
```python
class SnapshotArray(object):

    def __init__(self, length):
        """
        :type length: int
        """
        self.ss = [[(0,0)] for _ in range(length)]
        self.ind = 0
    
    def set(self, index, val):
        """
        :type index: int
        :type val: int
        :rtype: None
        """
        if self.ss[index][-1][0] == self.ind:
            self.ss[index][-1] = (self.ind, val)
        else:
            self.ss[index].append((self.ind, val))
        

    def snap(self):
        """
        :rtype: int
        """
        self.ind += 1
        return self.ind - 1        

    def get(self, index, snap_id):
        """
        :type index: int
        :type snap_id: int
        :rtype: int
        """
        i = bisect.bisect_right(self.ss[index], (snap_id, float('inf'))) - 1
        return self.ss[index][i][1]
        


# Your SnapshotArray object will be instantiated and called as such:
# obj = SnapshotArray(length)
# obj.set(index,val)
# param_2 = obj.snap()
# param_3 = obj.get(index,snap_id)
```
