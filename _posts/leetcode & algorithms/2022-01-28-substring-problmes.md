---
title: Substring Problems in Leetcode
Author: Luna
layout: post
tags: [algorithm, sliding window, leetcode]
---

Some medium/hard problems can be solved by sliding window with the template like below:

```python
int/string findSubstring(self, source, target):
    start = 0
    end = 0
    counter = 0 # check whether the string is valid
    length = 0 # the length of substring

    # intialize the map to store the characters we need here,for python, we can use Counter
    dict_t = Counter(target)

    # go through the source string
    while end < len(source):
        if source[end] in target:
            # do something to modify counter
            ...
            dict_t[source[end]]-- # minus 1 since we include the source[end] in the substring


        while (counter condition):
            # for min length problem: update length to find minimum length

            # increase start to make it valid/invalid again
            if source[start] in target:
                if ...
                # modify counter here
                ...

                dict_t[source[start]] ++
        
        # for max problem: update length to find maximum length
    
    return length / source[head:head+length]

```

## Some Sample Problems

### Leetcode 3: Find Longest Substring without Repeat Chars

>Given a string s, find the length of the longest substring without repeating characters.

dict_t store the current substring characters,  move "start" pointer until s[start, end] is a correct answer.

> ⚠️ Pay attention here we compare the max length outside of the innter loop 

```python
Class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        start = 0
        end = 0
        length = 0
        counter = 0

        dict_t = {} # here we don't have a target, but we want all the values here to be 1

        while end < len(s):
            if s[end] in dict_t.keys():
                dict_t[s[end]] += 1
                if dict_t[s[end]] > 1:
                    counter += 1 # invalid chars
            else:
                dict_t[s[end]] = 1
            
            while counter > 0:
                if s[start] in dict_t.keys():
                    dict_t[s[start]] -= 1
                    # after minus 1, the s[start] becomes a valid key, we should minus the counter
                    if dict_t[s[start]] == 1:
                        counter -=1
                    start += 1
            length = max(length, end-start+1)

            end += 1
        
        return length

```

### Leetcode 76: Minimum Window Substring

>Given two strings s and t of lengths m and n respectively, return the minimum window substring of s such that every character in t (including duplicates) is included in the window. If there is no such substring, return the empty string "".
>
> Example 
> 
>Input: s = "ADOBECODEBANC", t = "ABC"
>
>Output: "BANC"

Simiar to the former question but a little bit different, we use dict_t to store the characters in target string t. Here we are trying to find the minimum window, when we move the "end" pointer we can usually get a qualified but not shortest substring. So, we need to move the "start" pointer to minimize the substring length -- we can keep moving the "start" pointer until the substring is not qualified anymore.

```python
Class Solution:
    def minimumWindowSubstring(self, s: str, t: str) -> str:
        start = 0
        end = 0
        length = sys.maxsize
        dict_t = Counter(t) # require chars in t
        counter = len(t) # total count of t
        head = 0 # since we need to return the substring, we need a head

        while end < len(s):
            if s[end] in dict_t.keys():
                dict_t[s[end]] -= 1
                if dict_t[s[end]] >= 0:
                    counter -= 1
            
            while counter == 0:
                if end - start < length:
                    head = start
                    length = end - start
                if s[start] in dict_t.keys():
                    dict_t[s[start]] += 1
                    if dict_t[s[start]] > 0:
                        counter += 1
                start += 1
            
            end += 1
        
        if length == sys.maxsize:
            return ""
        return s[head:head + length+1]
            

```

Thanks for the template summary by [leetcode 10-line template](https://leetcode.com/problems/minimum-window-substring/discuss/26808/Here-is-a-10-line-template-that-can-solve-most-'substring'-problems)

