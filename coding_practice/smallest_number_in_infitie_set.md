Location: https://leetcode.com/problems/smallest-number-in-infinite-set/description/?envType=study-plan-v2&envId=leetcode-75
# Question
You have a set which contains all positive integers [1, 2, 3, 4, 5, ...].

Implement the SmallestInfiniteSet class:

- SmallestInfiniteSet() Initializes the SmallestInfiniteSet object to contain all positive integers.
- int popSmallest() Removes and returns the smallest integer contained in the infinite set.
- void addBack(int num) Adds a positive integer num back into the infinite set, if it is not already in the infinite set.
 
# Example

## Example 1:

Input: ["SmallestInfiniteSet", "addBack", "popSmallest", "popSmallest", "popSmallest", "addBack", "popSmallest", "popSmallest", "popSmallest"]
[[], [2], [], [], [], [1], [], [], []]

Output: [null, null, 1, 2, 3, null, 1, 4, 5]

Explanation:
</br>SmallestInfiniteSet smallestInfiniteSet = new SmallestInfiniteSet();
</br>smallestInfiniteSet.addBack(2);    // 2 is already in the set, so no change is made.
</br>smallestInfiniteSet.popSmallest(); // return 1, since 1 is the smallest number, and remove it from the set.
</br>smallestInfiniteSet.popSmallest(); // return 2, and remove it from the set.
</br>smallestInfiniteSet.popSmallest(); // return 3, and remove it from the set.
</br>smallestInfiniteSet.addBack(1);    // 1 is added back to the set.
</br>smallestInfiniteSet.popSmallest(); // return 1, since 1 was added back to the set and
</br>                                   // is the smallest number, and remove it from the set.
</br>smallestInfiniteSet.popSmallest(); // return 4, and remove it from the set.
</br>smallestInfiniteSet.popSmallest(); // return 5, and remove it from the set.

Constraints:

- 1 <= num <= 1000
- At most 1000 calls will be made in total to popSmallest and addBack.
 

# My solution 
```python
class SmallestInfiniteSet(object):

    def __init__(self):
        self.con = list(range(1, 2000))
        

    def popSmallest(self):
        """
        :rtype: int
        """
        return self.con.pop(0)
        

    def addBack(self, num):
        """
        :type num: int
        :rtype: None
        """
        if num not in self.con:
            self.con.append(num)
        self.con = sorted(self.con)
        


# Your SmallestInfiniteSet object will be instantiated and called as such:
# obj = SmallestInfiniteSet()
# param_1 = obj.popSmallest()
```

# Others' solution
```python
class SmallestInfiniteSet:

    def __init__(self):
        self.heap=[]
        self.min_num=1
        
    def popSmallest(self) -> int:
        if self.heap:
            return heapq.heappop(self.heap)
        self.min_num+=1
        return self.min_num-1
        
    def addBack(self, num: int) -> None:
        if self.min_num>num and num not in self.heap:
            heapq.heappush(self.heap,num)
```
