---
title: Javascript Object
date: 17-11-2020
categories:
- Javascript
tags:
- front end
---

### Definition:
- Unordered data collection
- Key-Value Pair collection

 ```javascript
let obj = {'name': 'frank', 'age':18}
let obj = new Object({'name': 'frank'})
console.log({'name':'frank', 'age': 18})
```

### Details
- key name should is string, not identifier, it can include any characters
- quotation mark can be omitted, after omitting the quotation mark, the key name can only be represented according to the rules of the identifier
- when you omit the quotation mark, the key name is also string
- Each key is the property name of a object
- Each value is the property value of a object
```javascript
Object.keys(obj)=>["1","100","255","3.2","0.01","0.234"]
Object.keys(obj) // can get all the keys of that obj
```

### Variable as Property name
  ```javascript
  let a = 'xxx'
  var obj = {'a': 111}
  var obj = {[a]: 1111} === var obj = {xxx: 1111}
  ```
- **How to use variables as property name?**
    - Previously we use constant as the property name
    - ``` let p1 = 'name' ```
    - ```let obj = {p1: 'frank'} ``` here, the property name is ```'p1'```
    - ```let obj = {[p1]: 'frank'} ``` here, the property name is ```'name'```
- Compare:
    - if there is no [], the property name will automatically become the string
    - if add [], the property will try to find the value inside of the []
    - if the property name is not a string, it will be automatically transformed into a string

- Five Falsy Values
    - null, undefined, 0, NaN, ''
- 7 data types
    - number
    - string
    - bool
    - symbol
    - null
    - undefined
    - object

### The hidden Property in the Object
> <img src="../../../../../assets/images/hiddenObjectProperty.png" width="500" alt="hidden Object Property">
>


### Delete Property
```javascript
let obj = {name:'frank', age: 18}
obj.name = undefined

console.log(obj)
// result: {name: undefined, age: 18}

delete obj.name
console.log(obj)
// result: {age: 18}

delete obj['name']
// result: true

// check if you have deleted the property successfully or not
// true => property exists, false => property not exists
'name' in obj

name in obj
// result: false
// because name and 'name' are different things,
// we have never declared or defined or assigned any value to name before
// name without ''  is a variable
```
> <img src="../../../../../assets/images/DeleteProperty.png" width="500" alt="Delete Property">

### Read Property
```javascript
let obj = {name:'frank', age: 18}
Object.keys(obj)
//result: (2)["name","age"]
Object.values(obj)
//result: (2)["frank","18"]
Object.entries(obj)
//result:
// (2) [Array(2), Array(2)]
// 0: (2) ["name", "frank"]
// 1: (2) ["age", 18]
// length: 2
// __proto__: Array(0)
```

**When you want to see all the properties in a object, please use  ```Console.dir()```  to print out all the properties.**
```javascript
var obj = {name:'frank', age: 18}
undefined
console.dir(obj)
VM301:1
Object
  age: 18
  name: "frank"
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
> <img src="../../../../../assets/images/CheckAllProperties.png" width="500" alt="Check All Properties">

```javascript
 obj.hasOwnProperty('toString')  //result: false
  obj.hasOwnProperty('name')  //result: true
 ```

### More Explanation about Prototype
> <img src="../../../../../assets/images/Prototype.png" width="500" alt="Prototype">
> <img src="../../../../../assets/images/LookupProperty.png" width="500" alt="Look up Prototype">
> <img src="../../../../../assets/images/Emphasis.png" width="500" alt="Emphasis property">
> <img src="../../../../../assets/images/Emphasis2.png" width="500" alt="Emphasis property2">


### Add or Modify Property Values
  ```javascript
  // direct assign value
  let obj = {name: 'frank'}  //'name' is a string
  let obj.name = 'frank'  //'name' is a string
  obj['na' + 'name'] = 'frank'
  let key = 'frank'; obj[key] = 'frank'

  //assign value in batches
  Object.assign(obj, {p1:1, p2:2, p3:3, p4:4, p5: 5})
  ```

### Add or Modify Prototype - **Common Properties**
- #### We cannot modify or add common Properties by object itself
  ```javascript
  let obj = {}; let obj2 = {} // they have common 'toString'
  obj.toString = 'xxx'
  // you can change the toString value of the Object  obj, but this toString property now only belongs to obj, not belongs to any other Object like obj2

  obj2.toString  // it still on the common properties
  ```
- #### If you insist to modify or add value to the Prototype (Common Property)
  ```javascript
  obj.__proto__.toString = 'xxx'  //not recommend to use __proto__
  Object.prototype.toString = 'xxx'

  // ****** Generally, please don't modify the prototype, can cause a lot of problem
  ```
### Modify hidden Properties
- ####  Not recommend to use __proto__
  ```javascript
  let obj = {'name': 'frank'}
  let obj2 = {'name': 'jack'}
  let common = {kind: 'human'}
  obj.__proto__ = common
  obj2.__proto__ = common
  ```

- #### Recommend to use **Object.create()**
  ```javascript
  let obj = Object.create(common)
  obj.name = 'frank'
  let obj2 = Object.create(common)
  obj2.name = 'jack'

  //规范大概的意思是，要改就一开始就改，别后来再改
  // 需要修改本地属性的时候 如下:
  Object.assign(obj, {p1:1, p2,2})
  ```

 ### Code Rule
<img src="../../../../../assets/images/code_rule.png" width="500" alt="Code Rule">


