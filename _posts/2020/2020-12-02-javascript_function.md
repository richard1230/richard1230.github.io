---
title: Javascript Function
date: 02-12-2020
categories:
- Javascript
tags:
- front end
---

### Key concepts about function
- Call time
- Scope
- Closure
- Parameter
- Return value
- Call Stack
- Hoisting
- Arguments (except arrow function)
- This

<img src="../../../../../assets/images/Closure.png" width="400" alt="closure">
<img src="../../../../../assets/images/func_hoisting.png" width="400" alt="func_hoisting.png">
<img src="../../../../../assets/images/JS_FUNCTION1.png" width="400" alt="">
<img src="../../../../../assets/images/JS_FUNCTION2.png" width="400" alt="">



```javascript
function fn(){
  console.log(this)
}

// if you don't give any condition to the function, 'this' will point to the 'window'
```
### if you don't give any condition to the function, 'this' will point to the 'window'

####  We must use:
```javascript
let person = {name:'frank',
sayHi(){
  console.log(this.name)
  }
}
person.sayHi.call(person)
```
<img src="../../../../../assets/images/why_use_this.png" width="400" alt="why_use_this.png">

```javascript
function add(x, y){
  return x + y
}

add.call(undefined, 1,2)
// first value used to occupy the position
```

### Arrow Function
- **Regular function 'this' refers parent, left of the dot**
- **Arrow function refers to it's current surrounding scope**
```javascript
  // regular function
  const bob = {
    firstName: "bob",
    lastName: "smith",
    sayName: function() {
      const self = this
      setTimeout(function() {
        console.log(`Hello, my name is ${self.firstName} ${self.lastName}`);
      })
    }
  }
  bob.sayName()
  //result: Hello, my name is bob smith
```

```javascript
 // arrow function
  const bob1 = {
    firstName: "bob",
    lastName: "smith",
    sayName: function() {
      setTimeout(()=> {
        console.log(`Hello, my name is ${this.firstName} ${this.lastName}`);
      })
    }
  }
bob1.sayName()
// Hello, my name is bob smith

```

### Arrow Function Hoisting
```javascript
  // sayHi() is a normal function
  sayHi()
  const john = 'john'
  const peter = 'Peter'

  function sayHi(person = "Susan"){
    console.log(`Hi ${person}`)
  }

  // this is an arrow function, but called before it initialized
  sayHello()
  const sayHello = (person = "Bob") => console.log(`Hello ${person}`)
```
### Array Destructing
```javascript
  // Array destructing
  const friends = ['john', 'peter', 'bob', 'alice']

  const [a, b, x] = friends
  console.log(a, b, x);
```

### Object Destructing
```javascript
    // Object destructing
    const bob = {
      first: 'bob',
      last: 'sanders',
      city: 'chicago',
      siblings: {
        sister: 'jane'
      },
    }

    const {
      first: firstName,
      last,
      city,
      zip,
      hop,
      siblings: {sister: favoriteSibling},
    } = bob;

    console.log(firstName, last, city, hop,favoriteSibling)
```

### Static Scoping VS Dynamic Scoping
```javascript
function fn1(){

    function fn2(){
        console.log(a)
    }

    // when the fn2 function has a parameter, the final result will be  4
    // function fn2(a){
    // console.log(a)
    // }

    function fn3(){
        var a = 4
        fn2()
    }
    var a = 2
    return fn3
  }

    var fn = fn1()
    fn() // result: 2
```
**Answer:**
> 静态作用域，看定义的位置，跟在哪调用无关, fn2中没有a，就会去它定义的上一层中找，就是fn1中, 跟在哪调用无关，因为JS是静态作用域的，只看它在何处定义的.
>
> 我的想法是动态作用域的想法，会在运行时沿着调用链查找；但是JS规定的是静态作用域，一个变量定义的那一刻，作用域就已经确定了，跟调用毛关系没有






