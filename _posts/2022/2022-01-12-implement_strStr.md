---
title: Implement stStr()
date: 12-01-2022 
categories:
- Algorithm 
tags:
- Algorithm

---

#### Description

    Implement strStr().
    Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.
    
    Clarification:
    What should we return when needle is an empty string? This is a great question to ask during an interview.
    For the purpose of this problem, we will return 0 when needle is an empty string. This is consistent to C's strstr() and Java's indexOf().
    
    
    Example 1:
    
    Input: haystack = "hello", needle = "ll"
    Output: 2
    Example 2:
    
    Input: haystack = "aaaaa", needle = "bba"
    Output: -1
    Example 3:
    
    Input: haystack = "", needle = ""
    Output: 0
    Constraints:
    
    0 <= haystack.length, needle.length <= 5 * 104
    haystack and needle consist of only lower-case English characters.

#### Thinking

1. traverse the haystack string, find out if there is the one letter equal the first letter in the needle string
2. if true, we can slice the length that equal to the needle string from the letter we found in the haystack, compare
   them
3. if equal the index
3. otherwise, we always return -1

```javascript
 /**
 * @param {string} haystack
 * @param {string} needle
 * @return {number}
 */

let strStr = (haystack, needle) => {
    if (needle.length === 0) return 0
    let initial = needle[0]

    for (let i = 0; i < haystack.length; i++) {
      if (haystack[i] === initial) {
        if (haystack.slice(i, (i + needle.length)) === needle) {
          return i
        }
      }
    }
    return -1
  }
```