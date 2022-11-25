---
title: algo-post-template-to-follow
date: 2022-11-21 07:20:09
tags:
---


## Approach 1: Brute Force

### Intuition
---

Because a sequence could start at any number in nums, we can exhaust the entire search space by building as long a sequence as possible from every number.

### Algorithm
---

The brute force algorithm does not do anything clever - it just considers each number in nums, attempting to count as high as possible from that number using only numbers in nums. After it counts too high (i.e. currentNum refers to a number that nums does not contain), it records the length of the sequence if it is larger than the current best. The algorithm is necessarily optimal because it explores every possibility.


### Complexity Analysis
---

**Time complexity** : O(n^3)O(n3).

The outer loop runs exactly nn times, and because currentNum increments by 1 during each iteration of the while loop, it runs in O(n)O(n) time. Then, on each iteration of the while loop, an O(n)O(n) lookup in the array is performed. Therefore, this brute force algorithm is really three nested O(n)O(n) loops, which compound multiplicatively to a cubic runtime.

**Space complexit**y : O(1)O(1).

The brute force algorithm only allocates a handful of integers, so it uses constant additional space.


