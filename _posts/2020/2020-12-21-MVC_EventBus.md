---
title: MVC and Event Bus
date: 21-12-2020
categories:
- Javascript
tags:
- front end
---

### What is MVC, give code example.
> M: Model is used to store data and manipulate all the data.
>
> V: View is responsible for all UI interface.
>
> C: Controller is responsible for modifying data you want

```javascript
  const eventBus = $(window)
  // put all data related data into the Model
  const m = {
    data: {
      n: parseInt(localStorage.get('n'))
    },
    create(){},
    delete(){},
    update(data){
      Object.assign(m.data, data)
      eventBus.trigger('m:updated')
    },
    get(){}
  }


// put all view related code in the view
const v = {
  el:null,
  html: `<div...>`,
  init(container){
    v.el = $(container)
  },
  render(n){
    if(v.el.children.length !== 0) v.el.empty()
    $(v.html.replace('{{n}}',n).appendTo(v.el)
  }
}

// the code for modifying data
const c = {
  init(container){
    v.init(container)
    v.render(m.data.n)
    c.autoBindEvents()
    eventBus.on('m:updated', ()=>{
      v.render(m.data.n)
    })
  },
  events:{
    'click #add1':'add',
    'click #minus1':'minus',
  }
  add(){
    m.update({n: m.data.n + 1})
  },
  minus(){
    m.update({n: m.data.n -1})
  },
  autoBindEvents(){
    for(let key in c.events){
      c.el.on(something there)
    }
  }
}


```
### What API does EventBus include? What does those API use for? Code Example.
```const eventBus = (window); ```
> ({}) is an empty object, there is no need to fetch elements, it only fetch three o APIs, ```on``` event, ```off``` event, ```trigger``` event

>```eventBus.on(types, selector, data,fn)```
> ```eventBus.trigger(type, data)```

### What is Excel-Driven Programming?
- bind events automatically
- when we will bind a bunch of events, we will change these events into a hash table first, and then implement the auto-binding
```javascript
  const c {
    events : {
            'click #add1': 'add',
            'click #minus1': 'minus',
        },
        add(){
            m.data.n +=1;
        },
        minus(){
            thism.data.n -=1;
        },
        autoBindEvents(){
            for(let key in c.events){
                c.el.on(xx,xx,xx)
            }
  }
```

### How to understanding Module?
> The code forms a set of fixed templates, does not need the programmer to write code from scratch, can achieve most of the requirements of the work, rapid development becomes possible,
The cost is that the code sometimes doesn't use that much, it can be wasteful, or in very demanding cases, modularity can become a constraint

