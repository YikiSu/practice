Location: https://leetcode.com/problems/design-hashset/description/?envType=problem-list-v2&envId=linked-list
# Question
Design a HashSet without using any built-in hash table libraries.

Implement MyHashSet class:

void add(key) Inserts the value key into the HashSet.\
bool contains(key) Returns whether the value key exists in the HashSet or not.\
void remove(key) Removes the value key in the HashSet. If key does not exist in the HashSet, do nothing.

 
# Example

## Example 1:

Input\
["MyHashSet", "add", "add", "contains", "contains", "add", "contains", "remove", "contains"]\
[[], [1], [2], [1], [3], [2], [2], [2], [2]]

Output\
[null, null, null, true, false, null, true, null, false]

Explanation\
MyHashSet myHashSet = new MyHashSet();\
myHashSet.add(1);      // set = [1]\
myHashSet.add(2);      // set = [1, 2]\
myHashSet.contains(1); // return True\
myHashSet.contains(3); // return False, (not found)\
myHashSet.add(2);      // set = [1, 2]\
myHashSet.contains(2); // return True\
myHashSet.remove(2);   // set = [1]\
myHashSet.contains(2); // return False, (already removed)

## Constraints:

0 <= key <= 106\
At most 104 calls will be made to add, remove, and contains.
 

# My solution 
```python
import collections
class MyHashSet(object):

    def __init__(self):
        self.li = collections.defaultdict(int)

    def add(self, key):
        """
        :type key: int
        :rtype: None
        """
        self.li[key] += 1
        

    def remove(self, key):
        """
        :type key: int
        :rtype: None
        """
        if contains(self.li, key):
            self.li.pop(key)   
        

    def contains(self, key):
        """
        :type key: int
        :rtype: bool
        """
        if key in self.li.keys():
            return True
        else:
            return False
        


# Your MyHashSet object will be instantiated and called as such:
# obj = MyHashSet()
# obj.add(key)
# obj.remove(key)
# param_3 = obj.contains(key) 
```
