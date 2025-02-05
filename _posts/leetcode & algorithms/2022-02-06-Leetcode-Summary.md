---
title: Leetcode Progress Summary
Author: Luna
layout: post
mathjax: true
tags: [algorithm, leetcode]
---
## DP
- [70. Climbing Stairs](https://leetcode.com/problems/climbing-stairs/)
- [746. Min Cost Climbing Stairs](https://leetcode.com/problems/min-cost-climbing-stairs/)
- [1137. N-th Tribonacci Number](https://leetcode.com/problems/n-th-tribonacci-number/)
  - nums[i] = nums[i-1] + nums[i-2] + nums[i-3]
- [338. Counting Bits](https://leetcode.com/problems/counting-bits/)
  - p(x+b) = p(x) + 1, b = 2^m
- [118. Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/)
  - res = [[1] * i for i in range(1, numRows + 1)] 
  - res[i][j] = res[i-1][j-1] + res[i-1][j]
## Two Pointers

| Problem Title                                                                                                       | Status                                                                                                          | notes                                                              |
| ------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| [167. Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)          | ✅                                                                                                               | left & right pointer                                               |
| [11.Container With Most Water](https://leetcode.com/problems/container-with-most-water/)                            | ✅                                                                                                               | left & right pointer                                               |
| [15. 3 Sum](https://leetcode.com/problems/3sum/)                                                                    | ✅ [Solution](/2022/02/06/Two-Pointer/#leetcode-15-three-sum)                                                    | left & right pointer                                               |
| [16. 3 Sum Closest](https://leetcode.com/problems/3sum-closest/)                                                    |                                                                                                                 |                                                                    |
| [18. 4 Sum](https://leetcode.com/problems/4sum/)                                                                    | ✅ [Solution](/2022/02/06/Two-Pointer/#n-sum)                                                                    |                                                                    |
| [19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)             |                                                                                                                 |                                                                    |
| [26. Remove Duplicates From Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)       | Given a sorted array, remove the duplicates in the array such that each element appears only once.            ✅ |                           similar problem <br /> [82. Remove Duplicates from Sorted List II](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/)    <br />   [83. Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/) <br /> [1836. Remove Duplicates From an Unsorted Linked List](https://leetcode.com/problems/remove-duplicates-from-an-unsorted-linked-list/)   |
| [28. Implement strStr()](https://leetcode.com/problems/implement-strstr/)                                           | Return the index of the first occurrence of substring in a string                                             ✅ | **KMP** will be better                                             |
| [42. Traping Rain Watter](https://leetcode.com/problems/trapping-rain-water/)                                       | ✅                                                                                                               | Left & right pointer, Need more practice <br>             [11. Container With Most Water](https://leetcode.com/problems/container-with-most-water/)            |
| [75. Sort Colors](https://leetcode.com/problems/sort-colors/)                                                       | ✅[Solution](/2022/02/06/Two-Pointer/#leetcode-75-sort-colors)                                                   | Left & Right pointer                                               |
| [80. Remove Duplicates from Sorted Array II](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/) | Given a sorted array, remove the duplicates in the array such that each unique element appears at most twice  ✅ |
| [125. Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)                                            | ✅ Useful Python string methods: s.lower() s.isalpha() s.isnumeric() s.isalnum()                                 | Left & right pointer.                                              |
| [345. Reverse Vowels in String](https://leetcode.com/problems/reverse-vowels-of-a-string/)                          | ✅                                                                                                               | Left & right pointer  s is not changable, we should us s = list(s) |
| [532. K-diff Pairs in an Array](https://leetcode.com/problems/k-diff-pairs-in-an-array/)                            | Given an array of integers nums and an integer k, return the number of unique k-diff pairs in the array.      ✅ | fast & slow pointer                                                |
| [557. Reverse Words in a String III](https://leetcode.com/problems/reverse-words-in-a-string-iii/)                  | ✅                                                                                                               | fast & slow pointer, s[slow:fast] = reversed(s[slow:fast])         |
| [Leetcode 905. Sort Array By Parity](https://leetcode.com/problems/sort-array-by-parity/)                           | ✅                                                                                                               | fast & slow pointer                                                |
| [Leetcode 922. Sort Array By Parity II](https://leetcode.com/problems/sort-array-by-parity-ii/)                     | ✅                                                                                                               | even & odd pointer                                                 |
| [Leetcode 977 Squares of a Sorted Array](#leetcode-977-squares-of-a-sorted-array)                                   | ✅ [Solution](/2022/02/06/Two-Pointer/#leetcode-977-squares-of-a-sorted-array)                                   | left & right pointer.                                              |

- [532. K-diff Pairs in an Array](https://leetcode.com/problems/k-diff-pairs-in-an-array/) (fast and slow pointer)
  
### Linked List
- [1721. Swapping Nodes in a Linked List](https://leetcode.com/problems/swapping-nodes-in-a-linked-list/)

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
|[56. Merge Intervals](https://leetcode.com/problems/merge-intervals/)|[Solution](/2022/02/17/sweep-line/#56-merge-intervals)||
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
|[370. Range Addition](https://leetcode.com/problems/range-addition/)|| ✅  |
|[1094. Car Pooling](https://leetcode.com/problems/car-pooling/)|[Solution](/2022/02/17/meeting-rooms/#1094-car-pooling)|✅ Can also be solved via sweep line|
|[1109. Coporate Flight Bookings](https://leetcode.com/problems/corporate-flight-bookings/)|[solution](/2022/02/17/sweep-line/#1109-corporate-flight-bookings)|✅Can also be solved via sweep line|

## DP

|Title| Solution|Notes|
|--|--|--|
|[413. Arithmetic Slices](https://leetcode.com/problems/arithmetic-slices/)|||


## Tree Problems
### BST
- [938. Range Sum of BST](https://leetcode.com/problems/range-sum-of-bst/)
- [98. Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)
  - left_max < root.val < right_min
  - similar problem: [333. Largest BST Subtree](https://leetcode.com/problems/largest-bst-subtree/)
### Path
- [437. Path Sum III](https://leetcode.com/problems/path-sum-iii/)  (prefix_sum)
-  [124. Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/)✅
-  [129. Sum Root to Leaf Numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers/)✅
   -  [1022. Sum of Root To Leaf Binary Numbers](https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers/) - similar problem
### Ancestor
- [235. Lowest Common Ancestor of a Binary Search Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)
- [236. Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/) ✅
- [1026. Maximum Difference Between Node and Ancestor](/2022/02/26/trees/#1026-maximum-difference-between-node-and-ancestor)
- [1123. Lowest Common Ancestor of Deepest Leaves](/2022/02/26/trees/#1123-lowest-common-ancestor-of-deepest-leaves)
- [1483. Kth Ancestor of a Tree Node](https://leetcode.com/problems/kth-ancestor-of-a-tree-node/) ❓

### DFS
- [298. Binary Tree Longest Consecutive Sequence](https://leetcode.com/problems/binary-tree-longest-consecutive-sequence/)
- [549. Binary Tree Longest Consecutive Sequence II](https://leetcode.com/problems/binary-tree-longest-consecutive-sequence-ii/)
  - dfs return [inc, dec], inc means the longest length the array is increase
- [543. Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/)
  - depth problem

### Others
- [617. Merge Two Binary Trees](https://leetcode.com/problems/merge-two-binary-trees/)

## Binary Search
- [4. Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/)
- [33. Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/) (left = 0, right = len(nums) - 1 左闭右闭)
- [34. Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/) (left = -1, right = len(nums), 左开右开)
- [35. Search Insert Position](https://leetcode.com/problems/search-insert-position/)(left = -1, right = len(nums), [0,left] < target, [right, len(nums)] > target)
- [69. Sqrt(x)](https://leetcode.com/problems/sqrtx/)(左开右开, left is the largest which makes nums[i] * nums[i] < x)
- [74. Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/) 
  -  i, j = mid // row_len, mid % row_len
  -  Related probelm - [240. Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/) it's more complicated, and can be solved by divide and conquer.
- [153. Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)
- [154. Find Minimum in Rotated Sorted Array II](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/)
- [540. Single Element in a Sorted Array](https://leetcode.com/problems/single-element-in-a-sorted-array/) 
  - case1: nums[mid] == nums[mid-1]  
  - case2: nums[mid] == numd[mid+1]
- [875. Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/) 
  - left, right = 1, max(piles)
  - similar problem [1011. Capacity To Ship Packages Within D Days](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)
- [981. Time Based Key-Value Store](https://leetcode.com/problems/time-based-key-value-store/) Design problem
- [1539. Kth Missing Positive Number](https://leetcode.com/problems/kth-missing-positive-number/)
- [287. Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/) O(nlogn) - can solved by [slow and fast pointer](/2022/02/15/Linked-List/#287-find-the-duplicate-number) with O(n) time.

## DFS
### Graph DFS
- [133. Clone Graph](https://leetcode.com/problems/clone-graph/)

- [207. Course Schedule](https://leetcode.com/problems/course-schedule/)
  - construct a dict from prerequisites <course, List[pre]>
  - go through courses, 
    - return True if no prerequisites
    - return False if visit already
    - add course into visit set and dfs its children
    - set pre to [] if the course can be completed to avoid duplicate dfsß
    - remember to remove the course from visit 
- [130. Surrounded Regions](https://leetcode.com/problems/surrounded-regions/)
  - dfs and mark boarder 'O's, other 'O's can be changed to 'X'



### Islands
- [200. Number of Islands](https://leetcode.com/problems/number-of-islands/) - **high frequency** 
  - similar question [419. Battleships in a Board](https://leetcode.com/problems/battleships-in-a-board/)
  - [solution](/2022/03/15/DFS/#)
- [305. Number of Islands II](https://leetcode.com/problems/number-of-islands-ii/)
  - union find
-[694. Number of Distinct Islands](https://leetcode.com/problems/number-of-distinct-islands/)
- [695. Max Area of Island](https://leetcode.com/problems/max-area-of-island/)
- [1905. Count Sub Islands](https://leetcode.com/problems/count-sub-islands/)
- [463. Island Perimeter](https://leetcode.com/problems/island-perimeter/)
  - don't need DFS

### Topological Sort
- [210. Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)
- [269. Alien Dictionary](https://leetcode.com/problems/alien-dictionary/)
- [444. Sequence Reconstruction](https://leetcode.com/problems/sequence-reconstruction/)
- [310. Minimum Height Trees](https://leetcode.com/problems/minimum-height-trees/)
  - It can be considered as a graph problem
  - the roots should be in the longest path, and they are the center of the longest path


### Backtracking
- [79. Word Search](https://leetcode.com/problems/word-search/)
  - similar problem: [489. Robot Room Cleaner](https://leetcode.com/problems/robot-room-cleaner/)
- [22. Generate Parentheses](https://leetcode.com/problems/generate-parentheses/)
- [78. Subsets](https://leetcode.com/problems/subsets/)
  - [90. Subsets II](https://leetcode.com/problems/subsets-ii/)
- [46. Permutations](https://leetcode.com/problems/permutations/)
  - [47. Permutations II](https://leetcode.com/problems/permutations-ii/)
- [77. Combinations](https://leetcode.com/problems/combinations/)
  - [39. Combination Sum](https://leetcode.com/problems/combination-sum/)
- [784. Letter Case Permutation](https://leetcode.com/problems/letter-case-permutation/)
- [1087. Brace Expansion](https://leetcode.com/problems/brace-expansion/)

## Stack

- [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)
  
### Monotonic Stack (单调栈)
- [84. Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/) //TODO
- [456. 132 Pattern](https://leetcode.com/problems/132-pattern/) //TODO
- [496. Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)
- [739. Daily Temperatures](https://leetcode.com/problems/daily-temperatures/)
- [239. Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)
  - maintain a decreasing deque

## Greedy
- [881. Boats to Save People](https://leetcode.com/problems/boats-to-save-people/)
- [2224. Minimum Number of Operations to Convert Time](https://leetcode.com/problems/minimum-number-of-operations-to-convert-time/)

## Heap
- [347. Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)
  - python heap: heapq.nlargest(k, count.keys(), key=count.get)

## Some Tricks
- [31. Next Permutation](https://leetcode.com/problems/next-permutation/)

​
 