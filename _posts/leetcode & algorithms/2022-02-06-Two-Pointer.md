---
title: Two Pointer 
Author: Luna
layout: post
mathjax: true
tags: [algorithm, leetcode]
---
There are 3 types of two-pointer algorithms.
1. fast & slow pointers
2. left & right pointers
3. same interval pointers

## Fast & Slow Pointers

- Intialization: fast = 0, slow = 0
- Move: fast moves faster than slow
- Return: usually return the slow index

### Template
```python
fast, slow = 0, 0
while fast < len(nums): # not reach the end
    if (condition):
        slow += 1
        ...
    fast += 1
```

### Sample Problems:
#### Leetcode 26 [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

> Given an nums array sorted in non-decreasing order, remove the duplicates in-place such that each elements appears only once.\
> Example:\
> Input: nums = [1,1,2]\
> Output: 2, nums[1,2,_]

```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        slow, fast = 0, 0

        while fast < len(nums):
            if nums[fast] != nums[slow]:
                slow += 1
                nums[slow] = nums[fast]
            fast += 1
        
        return slow + 1
```


#### Leetcode 80 [Remove Duplicates from Sorted Array II](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/)
> Given an nums array sorted in non-decreasing order, remove the duplicates in-place such that each elements appears only once.\
> Example:\
> Input: nums = [1,1,1,2,2,3]\
> Output: 2, nums[1,1,2,2,3_]

```python
Class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        slow, fast = 0, 0

        curr  = 0
        count = 0
        while fast < len(nums):
            if nums[fast] == curr:
                count += 1
            else:
                curr = nums[fast]
                count = 1
            
            if count <= 2:
                nums[slow] = nums[fast]
                slow += 1 # slow moves only if count <= 2
            
            fast += 1 # fast moves in every iteration

        return slow
```


#### Leetcode 532 [K-diff Pairs in an Array](https://leetcode.com/problems/k-diff-pairs-in-an-array/)

>Given an array of integers nums and an integer k, return the number of unique k-diff pairs in the array.\
> A k-diff pair is an integer pair (nums[i], nums[j]), where the following are true:\
> 0 <= i < j < nums.length\
> |nums[i] - nums[j]| == k\
> Example:\
> Input: nums = [3, 1, 4, 1, 5], k = 2\
> Output: 2\
> Explanation: two k-diff pairs (1, 3) and (3, 5)

We can sort the numbers firstly,  then init two pointers left = 0, right =1
If nums[right] - nums[left] < k, which means we should move the right further to add the difference between nums[left] and nums[right]\
Else we shoud move the left pointer closer to the right one.
The last possible condition is nums[right] - nums[k] == 0, this is the pair we need. After adding 1 to the res, we should move the left pointer until nums[left-1] != nums[left] to avoid duplicate pairs.

```python
class Solution:
    def findPairs(self, nums: List[int], k: int) ->int:
        nums.sort()
        res = 0
        left, right = 0, 1

        while right < len(nums) and left < len(nums):
            if left == right or nums[right] - nums[left] < k:
                right += 1
            elif nums[right] - nums[left] > k:
                left += 1
            else:
                res += 1
                left += 1
                while left < len(nums) and nums[left] == nums[left-1]:
                    left += 1
        return res
```

## Left & Right Pointers

Initalize the left pointer with 0, right pointer with len(nums) - 1, move from the two sides into the center until they reach each other.

### Sample Problems
#### Leetcode 42 [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)
water[i] = min(max_left, max_right) - height[i]

How to calculate the max_left and max_right for ith height?\
We have left and right pointers, max_left is the maximum height from [0:left], max_right is the maximum height from [right:end]\
$max\\_left = max(max\\_left, height[left])$\
$max\\_right = max(max\\_right, height[right])$

If max_left < max_right, it means that the max_left determines the water[left], even though the max_right isn't the maximum height in [left:end], but we don't need that real maximum. 
Similarly, if max_right <= max_left, it means the max_right determines the water[right].

So we have below code:
```python
Class Solution:
    def trap(self, height: List[int]) -> int:
        if not height: return 0

        left, right = 0, len(height) - 1
        max_left, max_right = height[left], height[right]
        res = 0

        while left < right:
            max_left = max(max_left, height[left])
            max_right = max(max_right, height[right])

            if max_left < max_right:
                res += max_left - height[left]
                left += 1
            else:
                res += max_right - height[right]
                right -= 1
        
        return res
```
