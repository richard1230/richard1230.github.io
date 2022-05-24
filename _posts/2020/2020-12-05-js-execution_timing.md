---
title: Javascript Execution Timing
date: 05-12-2020
categories:
- Javascript
tags:
- front end
---


### 函数的执行时机

1. 解释为什么如下代码会打印 6 个 6
```javascript
let i = 0
for(i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
```

答： setTimeout会等到for loop的 i < 6 一直循环完，才会执行，setTimeout在这里就像个闹钟，只有等到 for loop循环完，setTimeout这个闹钟才会执行。

> ```setTimeout``` function in Javascript usually takes a callback function as an argument. A callback function is a function that is executed after another function finishes running. In this case, it will run after for loop finishes. At this point, ```i``` is already 5 when the ```console.log([array[i])``` is about to be executed. Due to the **Closure** of javascript, ```the console.log``` has access to the i = 5 which is defined as an other outer layer of the setTimeout.

2. 写出让上面代码打印 0、1、2、3、4、5 的方法
```javascript
for(let i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
```
