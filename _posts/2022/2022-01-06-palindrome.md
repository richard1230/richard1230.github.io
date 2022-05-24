---
title: Palindrome Number 
date: 06-01-2022 
categories:
- Algorithm 
tags:
- Algorithm
- Leetcode

---

#### Description

> Given an integer x, return true if x is palindrome integer.
> An integer is a palindrome when it reads the same backward as forward.
> For example, 121 is a palindrome while 123 is not.

    Example 1:
    Input: x = 121
    Output: true
    Explanation: 121 reads as 121 from left to right and from right to left.
    Example 2:
    
    Input: x = -121
    Output: false
    Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
    Example 3:
    
    Input: x = 10
    Output: false
    Explanation: Reads 01 from right to left. Therefore it is not a palindrome.

```javascript
const isPalindrome = (x) => {
  if(x < 0) return false
  return x === reversedInteger(x)
}

const reversedInteger = (x)=>{
  // declare a temporary container to store the reversed digits from x one by one
  const reversed = 0
  
  // truncate the digidts from Ones digit to Hundreds digit of x, 
  // x needs greater than 0 after each truncate
  while(x > 0){
    // key point: 'reversed' is the iterator
    // the % module function is used to get the number from Ones digit
    // 用取模工具依次取个位数，十位数，百位数
    reversed = reversed * 10 + x%10
    
    // this is used to remove the Ones digit from the x, 
    // and x will be a new shorter number and will be used the next time 
    // 然后 用Math.floor获截取个位数之后的值，直到最后都截取完
    x = Math.floor(x/10)
  }
  
  return reversed
}
```




