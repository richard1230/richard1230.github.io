---
title: Longest Common Prefix
date: 08-01-2022
categories:
- Algorithm
tags:
- Algorithm
---


#### Description

    Write a function to find the longest common prefix string amongst an array of strings.
    If there is no common prefix, return an empty string "".
    
    Example 1:
    
    Input: strs = ["flower","flow","flight"]
    Output: "fl"
    Example 2:
    
    Input: strs = ["dog","racecar","car"]
    Output: ""
    Explanation: There is no common prefix among the input strings.
    
    
    Constraints:
    
    1 <= strs.length <= 200
    0 <= strs[i].length <= 200
    strs[i] consists of only lower-case English letters.


#### Thinking
- Take the first item as the prefix, then compare with the next one with' indexOf()' method, if the prefix exists then compare it with the next one.  if the prefix not exists, reduce one character to continue to compare.

```javascript
const longestCommonPrefix = (strs) => {
  let longestPrefix = ''
  if(strs === null | strs.length === 0) return longestPrefix

  let index = 0
  // loop through the first string in the strs array
  // then compare each letter of remaining strings in the array 
  // important: consider the index outofBound, not every string item length in the strs array greater than index while in the loop

  for(let comparisonLetter of strs[0]){
    for(let i = 1; i < strs.length; i++){
      // string[0][comparisonIndex]: each letter in the first string of strs array
      // strs[i].chartAt(inedx): each letter in the remaining string 

      let currentWord = strs[i]
      let currentLetter = currentWord.charAt(index)
      if(index > currentWord.length || currentLetter !== comparisonLetter)
      {
        return longestPrefix
      }
    }

    // since we use the vertical comparison method, so we need to do the below step outside the inner for loop
    longestPrefix += comparisonLetter
    index++
  }
  return longestPrefix
};
```