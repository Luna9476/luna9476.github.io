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
