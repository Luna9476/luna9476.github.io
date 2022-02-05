---
title: Substring Problems in Leetcode - Sliding Window
Author: Luna
layout: post
mathjax: true
tags: [algorithm, sliding window, leetcode]
---
# Contents
- [Contents](#contents)
  - [Some Sample Problems](#some-sample-problems)
    - [Leetcode 3: Find Longest Substring without Repeat Chars](#leetcode-3-find-longest-substring-without-repeat-chars)
      - [Similar Problems with Leetcode 3](#similar-problems-with-leetcode-3)
    - [Leetcode 76: Minimum Window Substring](#leetcode-76-minimum-window-substring)
    - [Leetcode 30: Substring with Concatention of All Words](#leetcode-30-substring-with-concatention-of-all-words)
  - [Other Simple Problems](#other-simple-problems)
    - [Leetcode 567: Permutation in String](#leetcode-567-permutation-in-string)
    - [Leetcode 438: Find All Anagrams in a String](#leetcode-438-find-all-anagrams-in-a-string)
  - [References](#references)

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
        counter = 0
        length = 0
        dict_t = {}
        
        start = 0
        
        for end in range(len(s)):
            if s[end] in dict_t.keys():
                dict_t[s[end]] += 1
                if dict_t[s[end]] > 1:
                    counter += 1
            else:
                dict_t[s[end]] = 1
            
            while counter > 0:
                if s[start] in dict_t.keys():
                    dict_t[s[start]] -= 1
                    if dict_t[s[start]] == 1:
                        counter -= 1
                    start += 1
            
            length = max(length, end-start+1)
        
        return length

```

#### Similar Problems with Leetcode 3

- Leetcode 159: [Longest Substring with At Most Two Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-two-distinct-characters/)
- Leetcode 340: [Longest Substring with At Most K Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/)

### Leetcode 76: Minimum Window Substring

>Given two strings s and t of lengths m and n respectively, return the minimum window substring of s such that every character in t (including duplicates) is included in the window. If there is no such substring, return the empty string "".
>
> Example 
> 
>Input: s = "ADOBECODEBANC", t = "ABC"
>
>Output: "BANC"

Similar to the former question but a little bit different, we use dict_t to store the characters in target string t. Here we are trying to find the minimum window, when we move the "end" pointer we can usually get a qualified but not shortest substring. So, we need to move the "start" pointer to minimize the substring length -- we can keep moving the "start" pointer until the substring is not qualified anymore.

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


### Leetcode 30: [Substring with Concatention of All Words](https://leetcode.com/problems/substring-with-concatenation-of-all-words/)



Thanks for the template summary by [leetcode 10-line template](https://leetcode.com/problems/minimum-window-substring/discuss/26808/Here-is-a-10-line-template-that-can-solve-most-'substring'-problems)

## Other Simple Problems
For some questions, the substring length is unchangable.

### Leetcode 567: Permutation in String

> Given two strings s1 and s2, return true if s2 contains a permutation of s1.
> Example:
> Input: s1 = "ab", s2 = "eibdaooo"
> Output: True

counter: current number of chars that should be in substring\\
length: the total number of chars we should have in substring\\
dict_t: required number of each char

For the above example, the inital value of dict_t is:

| char | required number |
| ---- | --------------- |
| a    | 1               |
| b    | 1               |

When we move *start* forward, s2[start] should be removed from substring. \
Since we loose s2[start], we should add 1 to dict_t[s2[start]].If after adding 1,  current dict_t[s2[start]] is $\ge$ 1, it means that s2[start] contributes to counter, we should substract counter by 1.\
When we move *end* forward, s1[end] will be added into substring.\
If current dict_t[s2[end]] is larger than 1, it means that s2[end] will add a new qualified char into substring, we should add 1 to counter.


```python
Class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:
        counter = 0
        length = len(s1)
        dict_t = Counter(s1)

        if len(s1) > len(s2):
            return False
        
        for i in range(length):
            if s2[i] in s1:
                if dict_t[s2[i]] >= 1:
                    counter += 1
                dict_t[s2[i]] -= 1
        
        if counter == length:
            return True
        
        for start in range(len(s2) - length):
            end = start + length

            if s2[start] in s1:
                dict_t[s2[start]] += 1
                if dict_t[s2[start]]>= 1:
                    counter -= 1
            
            if s2[end] in s1:
                if dict_t[s2[end]] >= 1:
                    counter += 1
                dict_t[s2[end]] -= 1
            
            if counter == length:
                return True
        
        return False
```

### Leetcode 438: Find All Anagrams in a String
> Given two strings s and p, return an array of all the start indices of p's anagrams in s. An anagram is a word or phrase formed by rearranging the letters of a different word or phrase typically using all the original letters exactly once.
> Exampe:
> Input: s = "cbaebabacd", p = "abc"
> Output: [0, 6]

Similar to the question above, instead of returning boolean, we should store the indices.

counter/length/dict_t are the same.

```python
Class Solution:
    def findAnagrams(self, s: str, p: str) -> List[int]:
        counter = 0
        length = len(p)
        dict_t = Counter(p)

        # res to store indices
        res = []
        if len(p) > len(s):
            return res
        
        for i in range(length):
            if s[i] in p:
                if dict_t[s[i]] >= 1:
                    counter += 1
                dict_t[s[i]] -= 1
        if (counter == length):
            res.append(0)
        
        for start in range(len(s) - length):
            end = start + length

            if s[start] in p:
                dict_t[s[start]] += 1
                if dict_t[s[start]] >= 1:
                    counter -= 1
            
            if s[end] in p:
                if dict_t[s[end]] >= 1:
                    counter += 1
                dict_t[s[end]] -= 1
            if (counter == length):
                res.append(start+1)
        
        return res
```

## References

https://leetcode.com/problems/find-all-anagrams-in-a-string/discuss/92007/Sliding-Window-algorithm-template-to-solve-all-the-Leetcode-substring-search-problem.

https://github.com/labuladong/fucking-algorithm/blob/master/%E7%AE%97%E6%B3%95%E6%80%9D%E7%BB%B4%E7%B3%BB%E5%88%97/%E6%BB%91%E5%8A%A8%E7%AA%97%E5%8F%A3%E6%8A%80%E5%B7%A7.md