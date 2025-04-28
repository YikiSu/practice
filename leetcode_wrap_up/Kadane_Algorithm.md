# Kadane's Algorithm

## General
Kadane's Algorithm is a dynamic programming approach used to solve problems involving contiguous subarrays (sequences of adjacent elements in an array). Its primary purpose is to efficiently compute:

Maximum Subarray Sum (classic problem).

Minimum Subarray Sum (with slight modifications).

Problems where optimal contiguous segments matter.

## When to Use Kadane's Algorithm
Use it when:

The problem involves contiguous subarrays (not subsequences).

You need to optimize sum/product (or similar metrics) of a subarray.

A brute-force approach would be $O(n^2)$ and you need an $O(n)$ solution.

## Problem type:
1. Maximum sum subarray
2. Minimum sum subarray
3. Maximum product subarray
4. Longest subarray with sum ≤ k

## How It Works (Intuition)
1. Track two variables:

  - current_sum: Sum of the current subarray.
  - max_sum: Maximum sum found so far.

2. Decide at each step:

  - Extend the current subarray (current_sum += num), or
  - Restart a new subarray (current_sum = num) if extending reduces the sum.
