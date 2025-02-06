# Yelp OA questions

Delete all the "AB" or "BB" substring in the string and concatenate the rest. Return the smallest possible length of the string. 

# Example 1:
Input: "AABB"\
Output: 0\
Explanation: After removing "AB" from the middle, "AB" is left and therefore it is deleted.

# Example 2:
Input: "BABBA"\
Output: 1\
Explanation: After removing "AB" from the middle, "BBA" is left and therefore "BB is deleted. Only "A" is left

# Solution
```python
def remove_func(seq):
  curr = []
  for s in seq:
    if curr and (curr[-1]+s in ["AB","BB"]):
        curr.pop()
    else:
        curr.append(s)
  return len(curr)
```
