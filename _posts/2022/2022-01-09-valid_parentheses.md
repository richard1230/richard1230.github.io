---
title: Valid Parentheses 
date: 09-01-2022 
categories:
- Algorithm 
tags:
- Algorithm
---

#### Description

    Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.
    
    An input string is valid if:
    
    Open brackets must be closed by the same type of brackets.
    Open brackets must be closed in the correct order.

    Example 1:
    Input: s = "()"
    Output: true

    Example 2:
    Input: s = "()[]{}"
    Output: true

    Example 3:
    Input: s = "(]"
    Output: false
    
    Constraints:
    1 <= s.length <= 104
    s consists of parentheses only '()[]{}'.

#### Thinking
- use stack to store each item in the s string array

```javascript
// create a map
const map = {
  ')': '(',
  ']': '[',
  '}': '{'
}

const isValid = (s) => {
  let stack = []
  for (let i = 0; i < s.length; i++) {
    // when find the open parentheses push to the stack
    if (s[i] === '(' || s[i] === '{' || s[i] === '[') {
      stack.push(s[i])
      
      // when we find there is the counterpart of one kind of the parentheses
      // compare the last item in the stack with the map's value
      // if equal, it means we find the pair of parentheses
      // if not equal, we didn't find any pair of parentheses
    } else if (stack[stack.length - 1] === map[s[i]]) {
      stack.pop()
    } else {
      return false
    }
  }
  return !stack.length
}

```