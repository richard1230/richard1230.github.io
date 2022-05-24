---
title: Insertion Sort
date: 20-10-2021
categories:
- Algorithm
tags:
- Algorithm
- Sort
---

#### Thinking:

1. set a marker for the sorted section after the first element
2. repeat the following until unsorted section is empty:
   select the first unsorted element
   swap other elements to the right to create the correct position and shift the unsorted element
 

```javascript
let arr = [3, 11,5, 14, 6, 8, 23, 37, 20, 10, 7]

const InsertionSort = (arr) => {
  for (let i = 1; i < arr.length; i++) {
    let unsortedElement = arr[i] //selects the first unsorted element
    let j = i - 1 //previous sorted element

    while (j >= 0 && arr[j] > unsortedElement) {
      //把前面大的数字挪到后面去
      arr[j + 1] = arr[j] // this loop shifts all the elements to the right to create the correct position for unsorted element
      j - 1 // ready to compare with the previous sorted element when go to the next while loop
    }
    //把后面小的目标数字挪到前面一个位置
    //注意：while循环里最后 j--，下面一行是 j-- + 1  的结果
    arr[j + 1] = unsortedElement  // this inserts the unsorted element to its correct position
  }
  return arr
}

console.log(InsertionSort(arr))

```

<img src="../../../../../assets/images/insertionSort.jpg" width="500" alt="Domain Name">
