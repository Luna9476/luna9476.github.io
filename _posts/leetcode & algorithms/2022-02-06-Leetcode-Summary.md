---
title: Leetcode Progress Summary
Author: Luna
layout: post
mathjax: true
tags: [algorithm, leetcode]
---

## Two Pointers

| Problem Title                                                                                                       | Status                                                                                                          | notes                                                              |
| ------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| [167. Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)          | ✅                                                                                                               | left & right pointer                                               |
| [11.Container With Most Water](https://leetcode.com/problems/container-with-most-water/)                            | ✅                                                                                                               | left & right pointer                                               |
| [15. 3 Sum](https://leetcode.com/problems/3sum/)                                                                    | ✅ [Solution](/2022/02/06/Two-Pointer/#leetcode-15-three-sum)                                                    | left & right pointer                                               |
| [16. 3 Sum Closest](https://leetcode.com/problems/3sum-closest/)                                                    |                                                                                                                 |                                                                    |
| [18. 4 Sum](https://leetcode.com/problems/4sum/)                                                                    | ✅ [Solution](/2022/02/06/Two-Pointer/#n-sum)                                                                    |                                                                    |
| [19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)             |                                                                                                                 |                                                                    |
| [26. Remove Duplicates From Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)       | Given a sorted array, remove the duplicates in the array such that each element appears only once.            ✅ |                                                                    |
| [28. Implement strStr()](https://leetcode.com/problems/implement-strstr/)                                           | Return the index of the first occurrence of substring in a string                                             ✅ | **KMP** will be better                                             |
| [42. Traping Rain Watter](https://leetcode.com/problems/trapping-rain-water/)                                       | ✅                                                                                                               | Left & right pointer, Need more practice                           |
| [75. Sort Colors](https://leetcode.com/problems/sort-colors/)                                                       | ✅[Solution](/2022/02/06/Two-Pointer/#leetcode-75-sort-colors)                                                   | Left & Right pointer                                               |
| [80. Remove Duplicates from Sorted Array II](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/) | Given a sorted array, remove the duplicates in the array such that each unique element appears at most twice  ✅ |
| [125. Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)                                            | ✅ Useful Python string methods: s.lower() s.isalpha() s.isnumeric() s.isalnum()                                 | Left & right pointer.                                              |
| [345. Reverse Vowels in String](https://leetcode.com/problems/reverse-vowels-of-a-string/)                          | ✅                                                                                                               | Left & right pointer  s is not changable, we should us s = list(s) |
| [532. K-diff Pairs in an Array](https://leetcode.com/problems/k-diff-pairs-in-an-array/)                            | Given an array of integers nums and an integer k, return the number of unique k-diff pairs in the array.      ✅ | fast & slow pointer                                                |
| [557. Reverse Words in a String III](https://leetcode.com/problems/reverse-words-in-a-string-iii/)                  | ✅                                                                                                               | fast & slow pointer, s[slow:fast] = reversed(s[slow:fast])         |
| [Leetcode 905. Sort Array By Parity](https://leetcode.com/problems/sort-array-by-parity/)                           | ✅                                                                                                               | fast & slow pointer                                                |
| [Leetcode 922. Sort Array By Parity II](https://leetcode.com/problems/sort-array-by-parity-ii/)                     | ✅                                                                                                               | even & odd pointer                                                 |
| [Leetcode 977 Squares of a Sorted Array](#leetcode-977-squares-of-a-sorted-array)                                   | ✅ [Solution](/2022/02/06/Two-Pointer/#leetcode-977-squares-of-a-sorted-array)                                   | left & right pointer.                                              |

## Math Related Problems

| ProblemTitle                                                 | Content                                                                                                 | Status | notes                                                                                                                                   |
| ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------- | ------ | --------------------------------------------------------------------------------------------------------------------------------------- |
| [258. Add Digits](https://leetcode.com/problems/add-digits/) | Given an integer num, repeatedly add all its digits until the result has only one digit, and return it. | ✅      | $nums = d_0 + d_1*10 + ... + d_k * 10 ^ k$ <br />$ = (d_0 + d_1 + ... + d_k) + 9 * m$ <br /> $(d_0 + d_1 + ... + d_k) \% 9 = nums \% 9$ |
|[50. Pow(x, n)](https://leetcode.com/problems/powx-n/)|[Solution](/2022/02/26/Math/#50-powx-n)|✅      |Divide and Conquer|
|[191. Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/)|[Solution](/2022/02/26/Math/#191-number-of-1-bits)|similar problems: https://leetcode.com/problems/power-of-two/|Bit manipulation: n&(n-1)|
|[190. Reverse Bits](https://leetcode.com/problems/reverse-bits/)|||Bit manipulation: n & 1 \| ans << 1|

## String Problems

| Problem Title                                                                              | Status | Notes                                         |
| ------------------------------------------------------------------------------------------ | ------ | --------------------------------------------- |
| [14. Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)          | ✅      | LCP(S1...Sn) = LCP(LCP(LCP(S1,S2), S3)... Sn) |
| [151. Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/) | ✅      | " ".join(reversed(s.split()))                 |

## Sweep Line

| Title | Solution | Notes |
| ----- | -------- | ----- |
|[252. Meeting Rooms](https://leetcode.com/problems/meeting-rooms/)|[Solution](/2022/02/17/meeting-rooms/#252-meeting-rooms)||
|[253. Meeting Rooms II](https://leetcode.com/problems/meeting-rooms-ii/)|[Solution](/2022/02/17/meeting-rooms/#253-meeting-rooms-ii)||
|[56. Merge Intervals](https://leetcode.com/problems/merge-intervals/)|[Solution](/2022/02/17/meeting-rooms/#56-merge-intervals)||
|[57. Insert Interval](https://leetcode.com/problems/insert-interval/)|[Solution](/2022/02/17/meeting-rooms/#57-insert-interval)||
|[1094. Car Pooling](https://leetcode.com/problems/car-pooling/)|[Solution](/2022/02/17/meeting-rooms/#1094-car-pooling)||
|[1272.Remove Intervals](https://leetcode.com/problems/remove-interval/)|[Solution](/2022/02/17/meeting-rooms/#1272remove-intervals)||
|[435. Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/)| [Sweep Line Solution](/2022/02/17/meeting-rooms/#435-non-overlapping-intervals) <br> [DP Solution]()||
|[452. Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/)|[Solution](/2022/02/17/meeting-rooms/#452-minimum-number-of-arrows-to-burst-balloons)| Similar to the non-overlapping problem|
|[1288. Remove Covered Intervals](https://leetcode.com/problems/remove-covered-intervals/)|[Solution]()

## Diff Array

diff[i] means nums[i] - nums[i-1] => nums[i] = nums[i-1] + diff[i]

|Title| Solution|Notes|
|--|--|--|
|[370. Range Addition](https://leetcode.com/problems/range-addition/)|||
|[1094. Car Pooling](https://leetcode.com/problems/car-pooling/)|[Solution](/2022/02/17/meeting-rooms/#1094-car-pooling)|Can also be solved via sweep line|
|[1109. Coporate Flight Bookings](https://leetcode.com/problems/corporate-flight-bookings/)|[solution](/2022/02/17/sweep-line/#1109-corporate-flight-bookings)|Can also be solved via sweep line|

## DP
|Title| Solution|Notes|
|--|--|--|
|[413. Arithmetic Slices](https://leetcode.com/problems/arithmetic-slices/)|||


## Tree Problems
### BST
### Path
- [437. Path Sum III](https://leetcode.com/problems/path-sum-iii/)  (prefix_sum)
### Ancestor
- [235. Lowest Common Ancestor of a Binary Search Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)
- [236. Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)


​
 