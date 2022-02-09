---
title: Leetcode Progress Summary
Author: Luna
layout: post
mathjax: true
tags: [algorithm, leetcode]
---

## Two Pointers

| Problem Title | Content | Status | notes |
| ------------- | ------- | ------ | ----- ||
|[11.Container With Most Water](https://leetcode.com/problems/container-with-most-water/)|                                                                                                              | :white_check_mark  | left & right pointer |
| [15. 3 Sum](https://leetcode.com/problems/3sum/)                                                                      |                                                                                                              |                    |                      |
|[16. 3 Sum Closest](https://leetcode.com/problems/3sum-closest/)                                                     |                                                                                                              |                    |                      |
|[18. 4 Sum](https://leetcode.com/problems/4sum/)                                                                    |                                                                                                              |                    |                      |
| [19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)             |                                                                                                              |                    |                      |
| [26. Remove Duplicates From Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)       | Given a sorted array, remove the duplicates in the array such that each element appears only once.           | :white_check_mark: |                      |
|[28. Implement strStr()](https://leetcode.com/problems/implement-strstr/)|Return the index of the first occurrence of substring in a string|:white_check_mark:|**KMP** will be better|
|[42. Traping Rain Watter](https://leetcode.com/problems/trapping-rain-water/)||:white_check_mark:|Left & right pointer, Need more practice|
|  [80. Remove Duplicates from Sorted Array II](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/) | Given a sorted array, remove the duplicates in the array such that each unique element appears at most twice | :white_check_mark: |                      |
|[532. K-diff Pairs in an Array](https://leetcode.com/problems/k-diff-pairs-in-an-array/)|Given an array of integers nums and an integer k, return the number of unique k-diff pairs in the array.|:white_check_mark:|fast & slow pointer|

## Math Related Problems

| ProblemTitle                                                   | Content                                                                                                 | Status             | notes |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------ | ----- |
|[258. Add Digits](https://leetcode.com/problems/add-digits/) | Given an integer num, repeatedly add all its digits until the result has only one digit, and return it. | :white_check_mark: | $nums = d_0 + d_1*10 + ... + d_k * 10 ^ k$ <br />$ = (d_0 + d_1 + ... + d_k) + 9 * m$ <br /> $(d_0 + d_1 + ... + d_k) \% 9 = nums \% 9$|