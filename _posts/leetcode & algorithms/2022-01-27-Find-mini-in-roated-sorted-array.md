---
title: 153. Find Minimum in Rotated Sorted Array
author: Luna
tags: [algorithm, leetcode, binary search] 
layout: post
header-img: "img/post-bg-2015.jpg"
date: 2022-01-27
mathjax: true
---
> Leetcode 153 
> 
> Suppose an array of length n sorted in ascending order is rotated between 1 and n times. 
> 
> For example, the array nums = [0,1,2,4,5,6,7] might become:
> 
> [4,5,6,7,0,1,2] if it was rotated 4 times.
> 
> [0,1,2,4,5,6,7] if it was rotated 7 times.
> 
> Notice that rotating an array [a[0], a[1], a[2], ..., a[n-1]] 1 time results in the array [a[n-1], a[0], a[1], a[2], ..., a[n-2]].
>
> Given the sorted rotated array nums of unique elements, return the minimum element of this array. You must write an algorithm that runs in $O(log n)$ time.

## Intuition

The simplest way is to go through the array - time complexity is $O(n)$.

Since it's a sorted array (although rotated), we can consider the binary search to satisfy the $O(logn)$ complexity.

1. If nums[start] < nums[end], it means that nums is the longest sorted array from start to end, then we can return nums[start]
2. If nums[mid] <= nums[0], it means that the right half is sorted, and the minimum element is in the right half.
3. Else the left half is sorted, the minimum element is in the left half.

## Code Implementation
```python
class Solution:
    def findMin(self, nums: List[int]) -> int:
        start = 0
        end = len(nums) - 1

        while start < end:
            if nums[start] < nums[end]:
                return nums[start]
            
            mid = (int)(start + (end - start) / 2)

            if nums[mid] <= nums[0]:
                start = mid + 1
            else:
                end = mid
        
        return nums[end]
            
```