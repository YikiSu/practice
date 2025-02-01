Location: https://leetcode.com/problems/pairs-of-songs-with-total-durations-divisible-by-60/description/
# Question
You are given a list of songs where the ith song has a duration of time[i] seconds.

Return the number of pairs of songs for which their total duration in seconds is divisible by 60. Formally, we want the number of indices i, j such that i < j with (time[i] + time[j]) % 60 == 0.

# Example

## Example 1:

Input: time = [30,20,150,100,40]

Output: 3

Explanation: Three pairs have a total duration divisible by 60:
</br>(time[0] = 30, time[2] = 150): total duration 180
</br>(time[1] = 20, time[3] = 100): total duration 120
</br>(time[1] = 20, time[4] = 40): total duration 60

## Example 2:

Input: time = [60,60,60]

Output: 3

Explanation: All three pairs have a total duration of 120, which is divisible by 60.


Constraints:

- 1 <= time.length <= 6 * 104
- 1 <= time[i] <= 500
 

# My solution (follows instructions on solutions)
```python
from collections import defaultdict
class Solution(object):
    def numPairsDivisibleBy60(self, time):
        """
        :type time: List[int]
        :rtype: int
        """
        cnt = defaultdict(int)
        pairs = 0
        for t in time:
            key = t%60
            if key == 0:
                pairs += cnt[0]
            else:
                pairs += cnt[60-key]
            cnt[key] += 1
        return pairs
        
```
