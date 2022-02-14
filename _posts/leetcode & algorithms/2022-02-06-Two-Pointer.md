---
title: Two Pointer 
Author: Luna
layout: post
mathjax: true
tags: [algorithm, leetcode]
---

- [Fast & Slow Pointers](#fast--slow-pointers)
  - [Template](#template)
  - [Sample Problems:](#sample-problems)
    - [Leetcode 26 Remove Duplicates from Sorted Array](#leetcode-26-remove-duplicates-from-sorted-array)
    - [Leetcode 80 Remove Duplicates from Sorted Array II](#leetcode-80-remove-duplicates-from-sorted-array-ii)
    - [Leetcode 532 K-diff Pairs in an Array](#leetcode-532-k-diff-pairs-in-an-array)
  - [Left & Right Pointers](#left--right-pointers)
    - [Trap Water Problems](#trap-water-problems)
      - [Leetcode 42 Trapping Rain Water](#leetcode-42-trapping-rain-water)
    - [Leetcode 75 Sort Colors](#leetcode-75-sort-colors)
    - [Leetcode 977 Squares of a Sorted Array](#leetcode-977-squares-of-a-sorted-array)
    - [Sum problems](#sum-problems)
      - [LeetCode 1: Two Sum](#leetcode-1-two-sum)
      - [LeetCode 15: Three Sum](#leetcode-15-three-sum)
      - [N-Sum](#n-sum)
  
There are 3 types of two-pointer algorithms.
1. fast & slow pointers
2. left & right pointers
3. same interval pointers

# Fast & Slow Pointers

- Intialization: fast = 0, slow = 0
- Move: fast moves faster than slow
- Return: usually return the slow index

## Template
```python
fast, slow = 0, 0
while fast < len(nums): # not reach the end
    if (condition):
        slow += 1
        ...
    fast += 1
```

## Sample Problems:
### Leetcode 26 [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

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


### Leetcode 80 [Remove Duplicates from Sorted Array II](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/)
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


### Leetcode 532 [K-diff Pairs in an Array](https://leetcode.com/problems/k-diff-pairs-in-an-array/)

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

### Trap Water Problems
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

### Leetcode 75 [Sort Colors](https://leetcode.com/problems/sort-colors/)
>Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.
> We will use the integers 0, 1, and 2 to represent the color red, white, and blue, respectively.

This is a very classcical problem - [Dutch National Flag Problem](https://en.wikipedia.org/wiki/Dutch_national_flag_problem)

We can initialize three pointers - left, mid, right. Our goal is to divide the array by these three pointers:
- [0, left) all 0s
- [left, mid] all 1s
- [right, end] all 2s

```python
class Solution:
    def sortColors(self, nums: List[int]) -> None:

        left, mid, right = 0, 0, len(nums) - 1

        while mid <= right:
            if nums[mid] == 2:
                nums[mid], nums[right] = nums[right], nums[mid]
                right -= 1 # here we don't right move mid, because we still need to check what is swapped to the mid position
            elif nums[mid] == 0:
                nums[mid], nums[left] = nums[left], nums[mid]
                mid += 1 # here we need to move the mid pointer, since the number swapped to the mid position might also be 0
                left += 1
            else:
                mid += 1
```

### Leetcode 977 [Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/)

> Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.

> Input: nums = [-4,-1,0,3,10]\
>Output: [0,1,9,16,100]\
>Explanation: After squaring, the array becomes [16,1,0,9,100].\
> After sorting, it becomes [0,1,9,16,100].

Go from the start and end of the array (they must be larger than the middle numbers)

```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        n = len(nums)
        res = [0] * n
        left, right = 0, n - 1
        
        for i in range(n-1, -1, -1):
            if abs(nums[left]) > abs(nums[right]):
                res[i] = nums[left] ** 2
                left += 1
            else:
                res[i] = nums[right] ** 2
                right -= 1
            
        
        return res
```
### Sum problems
#### LeetCode 1: Two Sum
> Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
> **You may assume that each input would have exactly one solution, and you may not use the same element twice.**

This problem asks us to return the index of the number, so if we want to use two pointer to solve this problem, we should memorize the original index of each number before sorting.

(We can use **HashTable** for this problem.)
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        numbers = [
            (num, index)
            for index, num in enumerate(nums)
        ]

        numbers.sort()
        left, right = 0, len(numbers) - 1

        while left < right:
            curr_sum = numbers[left][0] + numbers[right][0]
            if curr_sum == target:
                return [numbers[left][1], number[right][1]]
            elif curr_sum < target:
                left += 1
            else:
                right -= 1
```

#### LeetCode 15: Three Sum
> Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.\
> **Notice that the solution set must not contain duplicate triplets.**\
> Input: nums = [-1,0,1,2,-1,-4]\
> Output: [[-1,-1,2],[-1,0,1]]

One of the solutions is Two Pointer. We have a nested loop.
The main loop, i goes from 0 to end of the array.
In the inner loop, we use two pointer to translate the problem into a two-sum problem - nums[left] + nums[right] == -nums[i].

One more thing we need to pay attention to is the duplicate numbers.
We should directly skip the duplicate numbers.

```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        def twoSum(nums:List[int], start: int, target: int) -> List[List[int]]:
            left, right = start, len(nums)-1
            while left < right:
                curr_sum = nums[left] + nums[right]
                if curr_sum == target:
                    ans.append([nums[start-1],nums[left], nums[right]])
                    left += 1
                    # skip duplicate numbers
                    while left < right and nums[left-1] == nums[left]:
                        left +=1
                    right -= 1
                elif curr_sum < target:
                    left += 1
                else:
                    right -= 1
        
        ans = []
        nums.sort()
        i = 0

        # main loop
        while i < len(nums):
            # inner loop
            twoSum(nums, i+1, -nums[i])
            i += 1
            # skip duplicate numbers
            while i < len(nums) and nums[i-1] == nums[i]:
                i+= 1
        
        return ans
```
#### N-Sum

```python
def fourSum(self, nums, target):
    nums.sort()
    results = []
    self.findNsum(nums, target, 4, [], results)
    return results

def findNsum(self, nums: List[int], target: int, N: int, result: List[int], results: List[List[int]]) -> List[List[int]]:
    if len(nums) < N or N < 2:
        return
    # two sum
    if N == 2:
        left, right = 0, len(nums) - 1
        while left < right:
            curr_sum = nums[left] + nums[right]
            if curr_sum == target:
                results.append(result + [nums[left]] + [nums[right]])
                left += 1
                right -= 1
                while left < right and nums[left] == nums[left - 1]:
                    left += 1
                while left < right and nums[right] == nums[right + 1]:
                    right -= 1
            elif curr_sum < target:
                left += 1
            else:
                right -= 1
    else:
        for i in range(0, len(nums)-N+1):
            if target < nums[i] * N or target > nums[-1] * N:
                break
            if i == 0 or i != 0 and nums[i] != nums[i-1]:
                self.findNsum(nums[i+1:], target - nums[i], N-1, result+[nums[i]], results)
```

Similar Problem: 
- [Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/) -- this problem's nums are sorted, so it's more suitable to use two pointer for this problem.
- [1099. Two Sum Less Than K](https://leetcode.com/problems/two-sum-less-than-k/)
- [18. 4Sum](https://leetcode.com/problems/4sum/)


