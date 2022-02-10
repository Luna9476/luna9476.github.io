---
title: Leetcode Progress Summary
Author: Luna
layout: post
mathjax: true
tags: [algorithm, leetcode]
---

## Two Pointers

| Problem Title| Content | Status  | notes|
| -------------| ------- | ----| ----------------------- |
[167. Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)||✅ | left & right pointer                     |
| [11.Container With Most Water](https://leetcode.com/problems/container-with-most-water/) |    | ✅ | left & right pointer|
| [15. 3 Sum](https://leetcode.com/problems/3sum/)|   | ✅ [Solution](/2022/02/06/Two-Pointer/#leetcode-15-three-sum)  | left & right pointer|  |
| [16. 3 Sum Closest](https://leetcode.com/problems/3sum-closest/)|            |                    |                                          |
| [18. 4 Sum](https://leetcode.com/problems/4sum/)|     | ✅ [Solution](/2022/02/06/Two-Pointer/#n-sum)            |    |
| [19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)             |                                                                                                              |                    |                                          |
| [26. Remove Duplicates From Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)       | Given a sorted array, remove the duplicates in the array such that each element appears only once.           | ✅ |                                          |
| [28. Implement strStr()](https://leetcode.com/problems/implement-strstr/)                                           | Return the index of the first occurrence of substring in a string                                            | ✅ | **KMP** will be better                   |
| [42. Traping Rain Watter](https://leetcode.com/problems/trapping-rain-water/)                                       |                                                                                                              | ✅ | Left & right pointer, Need more practice |
| [80. Remove Duplicates from Sorted Array II](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/) | Given a sorted array, remove the duplicates in the array such that each unique element appears at most twice | ✅ |                          
                |
| [532. K-diff Pairs in an Array](https://leetcode.com/problems/k-diff-pairs-in-an-array/)                            | Given an array of integers nums and an integer k, return the number of unique k-diff pairs in the array.     | ✅ | fast & slow pointer                      |

## Math Related Problems

| ProblemTitle                                                 | Content                                                                                                 | Status             | notes                                                                                                                                   |
| -------------- | ------------------------- | ------------------ | --------------------------------------------------------------------------------------------------------------------------------------- |
| [258. Add Digits](https://leetcode.com/problems/add-digits/) | Given an integer num, repeatedly add all its digits until the result has only one digit, and return it. | ✅ | $nums = d_0 + d_1*10 + ... + d_k * 10 ^ k$ <br />$ = (d_0 + d_1 + ... + d_k) + 9 * m$ <br /> $(d_0 + d_1 + ... + d_k) \% 9 = nums \% 9$ |