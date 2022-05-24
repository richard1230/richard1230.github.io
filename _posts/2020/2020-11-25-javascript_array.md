---
title: Javascript Array
date: 25-11-2020
categories:
- Javascript
tags:
- front end
---

### Create an Array

```javascript
  let arr = [1,2,3]
  let arr = new Array(1,2,3)
  let arr = new Array(3)

  // Transform
  let arr = '1,2,3'.split(',')
  let arr = '123'.split('')
  Array.from('123')
  Array.from({0:'a', 1: 'b', 2: 'c', 3: 'd', length:4})

  //Special occasion
  Array.from({0:'a',1:'b', 2:'c', 3:'d', length: 2})
  // result: (2)["a", "b"]
 ```
### Pseudo-Array
```javascript
  let arr = {0:'a',1:'b', 2:'c', 3:'d', length: 3}
  // here is the prototype chain of the pseudo-array arr
  {0: "a", 1: "b", 2: "c", 3: "d", length: 3}
  0: "a"
  1: "b"
  2: "c"
  3: "d"
  length: 3
  __proto__:
  constructor: ƒ Object()
  hasOwnProperty: ƒ hasOwnProperty()
  isPrototypeOf: ƒ isPrototypeOf()
  propertyIsEnumerable: ƒ propertyIsEnumerable()
  toLocaleString: ƒ toLocaleString()
  toString: ƒ toString()
  valueOf: ƒ valueOf()
  __defineGetter__: ƒ __defineGetter__()
  __defineSetter__: ƒ __defineSetter__()
  __lookupGetter__: ƒ __lookupGetter__()
  __lookupSetter__: ƒ __lookupSetter__()
  get __proto__: ƒ __proto__()
  set __proto__: ƒ __proto__()
```
```javascript
  let divList = document.querySelectorAll('div')
  //伪数组的原型链中没有数组的原型
  // change the divList to array
  let divList = Array.from(divList)
  console.dir(divList)

  // combine two array
  arr1.concat(arr2)
  //truncate a part from an array
  arr1.slice(1) // start from the second element
  arr1.slice(0) // truncate all

  // !!! JS only provide shallow COPY
```
<img src="../../../../../assets/images/array_delete_elements.png" width="400" alt="array delete elements">

```javascript
  // delete the head element
  let array = [1,2,3]
  array.shift() // 1
  console.log(array) //result: (2)[2,3]
  let array2 = [1,2,3]


  //delete the tail element
  array2.shift() // 3
  console.log(array2) //result: (2)[1, 2]
  // something has changed

  // delete middle elements
  let array3 = [1,2,3,4,5]
  array3.splice(2,2) // 3,4
  console.log(array3) //result: (2)[1, 2,5]


  // delete middle elements and add new elements
  let array4 = [1,2,3,4,5]
  array4.splice(2,1, 55,24,23,678) // 3,4
  console.log(array4) //result: (8) [1, 2, 55, 24, 23, 678, 4, 5]
```

<img src="../../../../../assets/images/array_check_all_elements.png" width="400" alt="check all elements">
<img src="../../../../../assets/images/array_check_single_element.png" width="400" alt="check single element">
<img src="../../../../../assets/images/array_check_singe_2.png" width="400" alt="check single element">
<img src="../../../../../assets/images/array_add_element.png" width="400" alt="add element">
<img src="../../../../../assets/images/array_add_element2.png" width="400" alt="add element">
<img src="../../../../../assets/images/array_transform.png" width="400" alt="array_transform.png">



