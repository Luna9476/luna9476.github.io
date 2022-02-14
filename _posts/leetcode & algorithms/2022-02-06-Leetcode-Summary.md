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

## String Problems

| Problem Title                                                                              | Status | Notes                                         |
| ------------------------------------------------------------------------------------------ | ------ | --------------------------------------------- |
| [14. Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)          | ✅      | LCP(S1...Sn) = LCP(LCP(LCP(S1,S2), S3)... Sn) |
| [151. Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/) | ✅      | " ".join(reversed(s.split()))                 |
​
 