Location: (https://leetcode.com/problems/lemonade-change/description/)

# Question
At a lemonade stand, each lemonade costs $5. Customers are standing in a queue to buy from you and order one at a time (in the order specified by bills). Each customer will only buy one lemonade and pay with either a $5, $10, or $20 bill. You must provide the correct change to each customer so that the net transaction is that the customer pays $5.

Note that you do not have any change in hand at first.

Given an integer array bills where bills[i] is the bill the ith customer pays, return true if you can provide every customer with the correct change, or false otherwise.

# Example
## Example 1:

Input: bills = [5,5,5,10,20]

Output: true

Explanation: 
- From the first 3 customers, we collect three $5 bills in order.
- From the fourth customer, we collect a $10 bill and give back a $5.
- From the fifth customer, we give a $10 bill and a $5 bill.
- Since all customers got correct change, we output true.
 
## Example 2:

Input: bills = [5,5,10,10,20]

Output: false

Explanation: 
- From the first two customers in order, we collect two $5 bills.
- For the next two customers in order, we collect a $10 bill and give back a $5 bill.
- For the last customer, we can not give the change of $15 back because we only have two $10 bills.
- Since not every customer received the correct change, the answer is false.

# My answer (time limit exceeds, follows solutions)
```python 
class Solution(object):
    def lemonadeChange(self, bills):
        """
        :type bills: List[int]
        :rtype: bool
        """
        five = 0
        ten = 0
        for bill in bills:
            # print(five)
            # print(ten)
            # print(f"five is {five}")
            # print(f"ten is {ten}")
            if bill == 5:
                five += 1
            elif bill == 10:
                if five > 0:
                    five -= 1
                    ten += 1
                else:
                    return False
            else:
                if five > 0 and ten > 0:
                    five -=1
                    ten -=1
                elif five > 2:
                    five -=3
                else:
                    return False
        return True
```

