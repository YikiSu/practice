Location: https://leetcode.com/problems/minimum-index-sum-of-two-lists/description/
# Question
Given two arrays of strings list1 and list2, find the common strings with the least index sum.

A common string is a string that appeared in both list1 and list2.

A common string with the least index sum is a common string such that if it appeared at list1[i] and list2[j] then i + j should be the minimum value among all the other common strings.

Return all the common strings with the least index sum. Return the answer in any order.
# Example

## Example 1:

Input: list1 = ["Shogun","Tapioca Express","Burger King","KFC"], list2 = ["Piatti","The Grill at Torrey Pines","Hungry Hunter Steakhouse","Shogun"]

Output: ["Shogun"]

Explanation: The only common string is "Shogun".

## Example 2:

Input: list1 = ["Shogun","Tapioca Express","Burger King","KFC"], list2 = ["KFC","Shogun","Burger King"]

Output: ["Shogun"]

Explanation: The common string with the least index sum is "Shogun" with index sum = (0 + 1) = 1.

## Example 3:

Input: list1 = ["happy","sad","good"], list2 = ["sad","happy","good"]

Output: ["sad","happy"]

Explanation: There are three common strings:\
"happy" with index sum = (0 + 1) = 1.\
"sad" with index sum = (1 + 0) = 1.\
"good" with index sum = (2 + 2) = 4.\
The strings with the least index sum are "sad" and "happy".

## Constraints:

1 <= list1.length, list2.length <= 1000\
1 <= list1[i].length, list2[i].length <= 30\
list1[i] and list2[i] consist of spaces ' ' and English letters.\
All the strings of list1 are unique.\
All the strings of list2 are unique.\
There is at least a common string between list1 and list2.
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def findRestaurant(self, list1, list2):
        """
        :type list1: List[str]
        :type list2: List[str]
        :rtype: List[str]
        """
        ans = []
        smallest = float("inf")
        dict1 = {st:ind for ind, st in enumerate(list1)}
        dict2 = {st:ind+dict1[st] for ind, st in enumerate(list2) if st in dict1.keys()}
        for key, value in dict2.items():
            if value < smallest:
                ans = [key]
                smallest = value
            elif smallest == value:
                ans.append(key)
        return ans


        # if len(list1) > len(list2):
        #     a = list1
        #     b = list2
        # else:
        #     a = list2
        #     b = list1
        # for ind, st in enumerate(a):
        #     if st in b:
        #         indb = b.index(st)
        #         if ind + indb < smallest:
        #             ans = [st]
        #             smallest = ind + indb
        #         elif ind + indb == smallest:
        #             ans.append(st)
        # return ans

        # dic = {}
        # for ind, st in enumerate(list1):
        #     dic[st] = [ind]
        # for ind, st in enumerate(list2):
        #     if st in dic.keys():
        #         dic[st].append(ind)
        #     else:
        #         dic[st] = [ind]
        # ans = []
        # smallest = float("inf")
        # for key, value in dic.items():
        #     # print(key)
        #     # print(value)
        #     if len(value)==2:
        #         print('entering')
        #         if sum(value) < smallest:
        #             ans = [key]
        #             smallest = sum(value)
        #         elif sum(value) == smallest:
        #             ans.append(key)
        #     # print(ans)
        # return ans

```
