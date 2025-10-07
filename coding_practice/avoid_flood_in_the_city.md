Location: https://leetcode.com/problems/avoid-flood-in-the-city/description/?envType=daily-question&envId=2025-10-07
# Question
Your country has an infinite number of lakes. Initially, all the lakes are empty, but when it rains over the nth lake, the nth lake becomes full of water. If it rains over a lake that is full of water, there will be a flood. Your goal is to avoid floods in any lake.

Given an integer array rains where:

- rains[i] > 0 means there will be rains over the rains[i] lake.
- rains[i] == 0 means there are no rains this day and you can choose one lake this day and dry it.

Return an array ans where:

- ans.length == rains.length
- ans[i] == -1 if rains[i] > 0.
- ans[i] is the lake you choose to dry in the ith day if rains[i] == 0.

If there are multiple valid answers return any of them. If it is impossible to avoid flood return an empty array.

Notice that if you chose to dry a full lake, it becomes empty, but if you chose to dry an empty lake, nothing changes.

 
# Example

## Example 1:

Input: rains = [1,2,3,4]

Output: [-1,-1,-1,-1]

Explanation: After the first day full lakes are [1]\
After the second day full lakes are [1,2]\
After the third day full lakes are [1,2,3]\
After the fourth day full lakes are [1,2,3,4]\
There's no day to dry any lake and there is no flood in any lake.

## Example 2:

Input: rains = [1,2,0,0,2,1]

Output: [-1,-1,2,1,-1,-1]

Explanation: After the first day full lakes are [1]\
After the second day full lakes are [1,2]\
After the third day, we dry lake 2. Full lakes are [1]\
After the fourth day, we dry lake 1. There is no full lakes.\
After the fifth day, full lakes are [2].\
After the sixth day, full lakes are [1,2].\
It is easy that this scenario is flood-free. [-1,-1,1,2,-1,-1] is another acceptable scenario.

## Example 3:

Input: rains = [1,2,0,1,2]

Output: []

Explanation: After the second day, full lakes are  [1,2]. We have to dry one lake in the third day.\
After that, it will rain over lakes [1,2]. It's easy to prove that no matter which lake you choose to dry in the 3rd day, the other one will flood.
 

## Constraints:

1 <= rains.length <= 105\
0 <= rains[i] <= 109
 

# My solution (follows instructions on solutions)
```python
import collections
from sortedcontainers import SortedList

class Solution(object):
    def avoidFlood(self, rains):
        """
        :type rains: List[int]
        :rtype: List[int]
        """
        n = len(rains)
        res = [-1] * n
        lakes = collections.defaultdict(int)  # Track last rain day for each lake
        dry_days = SortedList()  # Sorted list of dry day indices
        
        for i, lake in enumerate(rains):
            if lake == 0:
                dry_days.add(i)  # O(log k)
                res[i] = 1  # Default: dry any lake
            else:
                if lake in lakes:
                    last_rain = lakes[lake]
                    # Find earliest dry day after last_rain
                    idx = dry_days.bisect_right(last_rain)
                    if idx >= len(dry_days):
                        return []  # No dry day available
                    dry_day = dry_days.pop(idx)  # O(log k)
                    res[dry_day] = lake  # Dry this lake
                    lakes[lake] = i
                else:
                    lakes[lake] = i
        
        return res
# import collections
# class Solution(object):
#     def avoidFlood(self, rains):
#         """
#         :type rains: List[int]
#         :rtype: List[int]
#         """
#         res = [-1] * len(rains)
#         lakes = collections.defaultdict(int)
#         dry = []
#         for ind, r in enumerate(rains):
#             if r == 0:
#                 # dry.append(ind)
#                 bisect.insort(dry, ind)
#                 res[ind] = 1
#             else:
#                 if r in lakes.keys():
#                     day = lakes[r]
#                     idx = bisect.bisect_right(dry, day)
#                     if idx >= len(dry):
#                         return []
#                     else:
#                         dry_day = dry.pop(idx)
#                         res[dry_day] = r
#                         lakes[r] = ind
#                 else:
#                     lakes[r] = ind
#         return res

        
```
