---
title: Tagged Template
date: 18-12-2020
categories:
- Javascript
tags:
- front end
---

**Example 1**
```javascript
  let person = 'Mike'
  let age = 28

  function myTag(strings, personExp, ageExp){
    let str0 = strings[0] // "That "
    let str1 = strings[1] // " is a "

    // There is technically a string after the final expression (in our example),
    // but it is empty ("empty"), so disregard. let str2 = strings[2]

    let ageStr
    if(ageExp > 9){
      ageStr = 'centenarian'
    }else{
      ageStr = 'youngster'
    }
  }

  // we can even return a string built using a template literal
  return `${str0}${personExp}${str1}${ageStr}`
}

  let output = myTag`That ${person} is a ${age}`
  console.log(output)
  // result: That Mike is a youngster
```

**Example 2**
```javascript
  const author = "Some Author"
  const statement = "Some Statement"
  const third = "Last One"

  var quote = highlight`Here is the ${statement} by ${author} and it could not be more true ${third}`
  console.log(quote)

  // function highlight(text, arg1, arg2){
  //   console.log(text)
  //   console.log(arg1)
  //   console.log(arg2)
  //   console.log({text, arg1,arg2})
  // }


  // advanced code
  function highlight(text, ...vars){
    console.log({text, vars})
  }
  // result
  // {text: Array(4), vars: Array(3)}
  // text: (4) ["Here is the ", " by ", " and it could not be more true ", "", raw: Array(4)]
  // vars: (3) ["Some Statement", "Some Author", "last one"]
  // __proto__: Object


// more advanced code with rest operator
function highlight(text, ...vars){
  const awesomeText = text.map(item, index) => {
    return `${item} <strong class="blue">${vars[index] || ""} </strong>`
  }
  return awesomeText,join("")
}
```

