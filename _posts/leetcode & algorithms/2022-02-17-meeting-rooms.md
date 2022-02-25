---
title: Meeting Room Related Problems
layout: post
mathjax: true
tags: [algorithm, leetcode]
---
## Interval & Sweep Line Related Problems
![](/img/leetcode/duplicate%20intervals.jpeg)

For two intervals,  A and B:
- if A.end > B.start and
- A.start < B.end 

then they have duplicate intervals.

After sorting by the start time, we are sure that A.start < B.end, which means if A.end > B.start then they have duplicate intervals.


## [252. Meeting Rooms](https://leetcode.com/problems/meeting-rooms/)
Given an array of meeting time intervals consisting of start and end times[[s1,e1],[s2,e2],...](si< ei), determine if a person could attend all meetings.

We can sort the intervals by the starting time. Then go through the meetings one by one and make sure that each meeting ends before the next one starts.

```python
class Solution:
    def canAttendMeetings(self, intervals: List[List[int]]) -> bool:
        intervals.sort(key = lambda x: x[0])

        for i in range(len(intervals) - 1):
            if intervals[i][1] > intervals[i+1][0]:
                return False
        
        return True
```

## [56. Merge Intervals](https://leetcode.com/problems/merge-intervals/)
Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

This problem is similar with the Meeting Rooms problem, except for we need to merge when we find the duplicated part.

```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        intervals.sort(key = lambda x: x[0])

        res = []

        for i in range(len(intervals)):
            if not res or res[-1][1] < intervals[i][0]:
                res.append(intervals[i])
            else:
                res[-1][1] = max(res[-1][1], intervals[i][1])
        return res
```

## [253. Meeting Rooms II](https://leetcode.com/problems/meeting-rooms-ii/)

Given an array of meeting time intervals intervals where intervals[i] = [starti, endi], return the minimum number of conference rooms required.

We can use swipe line for this question.
![image from labuladong](/img/leetcode/sweep%20line.jpeg)

```python
class Solution:
    def minMeetingRooms(self, intervals: List[List[int]]) -> int:
        if not intervals:
            return 0
        start_timings = sorted(interval[0] for interval in intervals)
        end_timings = sorted(interval[1] for interval in intervals)

        start = end = 0
        count = 0
        max_lap = 0
        while start < len(intervals) and end < len(intervals):
            start_timing, end_timing = start_timings[start], end_timings[end]
            if start_timing <= end_timing :
                count += 1
                start += 1
            
            if end_timing <= start_timing:
                count -= 1
                end += 1
            
            max_lap = max(max_lap, count)
        
        return max_lap

```
### Follow Up Question

1. Return the interval which is max overlapped.
we can store the start time whenever we meet the maximum count, and the end time is the next first end time we meet.

2. Google: Given a list of intervals calendar and a number of available conference rooms. For each query, return true if the meeting can be added to the calendar successfully without causing a conflict, otherwise false. A conference room can only hold one meeting at a time.\
   Input: calendar = [[1, 2], [4, 5], [8, 10]], rooms = 1, queries = [[2, 3], [3, 4]] \
   Output: [true, true]

## [57. Insert Interval](https://leetcode.com/problems/insert-interval/)

Given an existing non-overlapping interval list sorted by start, insert a new interval into it, merge if needed.

Input: intervals = [[1,3],[6,9]], newInterval = [2,5]\
Output: [[1,5],[6,9]]

![](/img/leetcode/insert-interval.jpeg)
- firstly, we find out the interval whose end is larger than the new inserted interval start (the first overlapping interval)
- start from this first overlapping interval, we find the last overlapping interval, whose start <= new interval's end

```python
class Solution:
    def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]
        i = 0
        while i < len(intervals) and intervals[i][1] < newInterval[0]:
            i += 1
        
        while i < len(intervals) and intervals[i][0] <= newInterval[1]:
            newInterval[0] = min(intervals[i][0], newInterval[0])
            newInterval[1] = max(intervals[i][1], newInterval[1])
            intervals.remove(intervals[i])
        intervals.insert(i, newInterval)
        return intervals
```

## [1094. Car Pooling](https://leetcode.com/problems/car-pooling/)
A car with *capacity* seats. Given an array *trips* where trips[i] = [numPassengers, from, to] indicates that the ith trip has numPassengers and the location to pick them up is from, drip off is to.
Return True if it's possible to pick all passengers for all the given trips, or False otherwise.

Example:\
Input: trips = [[2,1,5],[3,3,7]], capacity = 4\
Output: false
![](/img/leetcode/carpool.jpeg)

```python
class Solution:
    def carPooling(self, trips: List[List[int]], capacity: int) -> bool:
        timestamp = []
        for trip in trips:
            timestamp.append(trip[1], trip[0])
            timestamp.append(trip[2], -trip[0])
        
        timestamp.sort()

        used = 0
        for time, passenger_change in timestamp:
            used += passenger_change
            if used > capacity:
                return False
        
        return True
```
