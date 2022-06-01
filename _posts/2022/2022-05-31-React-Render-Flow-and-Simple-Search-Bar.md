---
title: React Render Flow and Simple Search Bar
date: 31-05-2022 
categories:
- React 
tags:
- React
---


## Build Project
```shell
npx create-react-app monsters-rolodex
cd monsters-rolodex
yarn start
yarn add cowsay
```

## npx

test:

```shell
cowsay hello
 _______
< hello >
 -------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||


npx cowsay hello
 _______
< hello >
 -------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

npx: we can use npx to download the package , the latest version of it, and it deleted the package after using it;

## React大致渲染流程(render flow about React)

- regardless of whether this is React or JavaScript, classes will always run the constructor function first inside of
  here.

- The render runs next, and what it does is the render determines what to show. This you can see kind of as the template
  of the HTML, so this dictates what the UI for this component is going to be.

- Then the next life cycle that runs is componentDidMount, I run the constructor of initialize the state, the initial
  state at the very least, and I am going to now render the initial UI of this component. So it's actually going to
  mount this initial UI onto the Dom.
  what this means is that whatever the initial state of your component is, is what it will mount on.
  And here we are fetching some JSON.
  This is asynchronous, so we actually don't know when this data is going to come back.
  Once it comes back, we are going to now update the state.
  But the moment that that state updates remember, the moment state changes and you've called set state.

- call the render again

### summary

Run the constructor, run the initial render when your initial monster's value was an empty array.

Then, once your component mounts fetch, the new users call that state and once again, once the state gets called Call
Render Again and now Component is the new updated users list.

- constructor runs first, initialize your state,

- render your initial component UI.

- Then once you need some API, calls to it in the component at Mount lifecycle. Once that happens, you want to set state
  to make sure that your component updates.

- And once it(component) updates, it's going to call render again to re render the UI.

That's the flow:

Run the constructor --->Run render() ---> componentDidMount -----> Run render() again

## 写搜索框功能的时候的注意点

- 要将被搜索的字符串写在state里面
- 结合使用`filter()`,`includes()`函数

```Jsx
import React from 'react';

class App extends React.Component {
  constructor() {
    super();
    this.state = {
      monsters: [],
      searchField: ''
    }
    console.log("constructor: " + 1)
  }

  componentDidMount() {
    console.log("componentDidMount: " + 3)
    fetch(
      'https://jsonplaceholder.typicode.com/users'
    ).then((response) => response.json())
      .then(users => this.setState(
        () => {
          return { monsters: users }
        }
      )
      )

  }


  render() {
    console.log("render: " + 2)
    const filterMonsters = this.state.monsters.filter(
      (monster) => monster.name.toLowerCase().includes(this.state.searchField)
      //注意:filter也是返回对象,这里的逻辑是筛选出输入框中外部输出的包含字符串的name
    )

    console.log("filterMonsters:===》" + filterMonsters)

    return (
      <div className="App">
        <input
          className='search-box'
          type='search'
          placeholder='search monsters'
          onChange={
            (e) => {

              const searchField = e.target.value.toLowerCase();
              this.setState(
                // () => { 
                // return {searchField }
                // }
                //two methods are equal
                { searchField: searchField }
              )
            }
          }
        />
        {
          filterMonsters.map((monster) => {
            return (<div key={monster.id}>
              <h1>{
                monster.name
              }
              </h1>
            </div>)
          })
        }
      </div>
    );
  }
}

export default App


```

## Optimizations about performance

[see the code](https://github.com/richard1230/monsters-rolodex/commit/968e91569a90ff7d9a93f304c05a6ddef289fa5f):<br>
before Optimization:

```jsx
render()
{
  const filterMonsters = this.state.monsters.filter(
    (monster) => monster.name.toLowerCase().includes(this.state.searchField)
  )


  return (
    <div className="App">
      <input
        className='search-box'
        type='search'
        placeholder='search monsters'
        onChange={
          (e) => {

            const searchField = e.target.value.toLowerCase();
            this.setState(
              {searchField: searchField}
            )
          }
        }
      />
      {
        filterMonsters.map((monster) => {
          return (<div key={monster.id}>
            <h1>{
              monster.name
            }
            </h1>
          </div>)
        })
      }
    </div>
  );
}
```

after Optimization:

```jsx

onSearchChange = (e) => {
  const searchField = e.target.value.toLowerCase();
  this.setState(
    {searchField: searchField}
  )
}


render()
{
  const {monsters, searchField} = this.state;
  const {onSearchChange} = this;
  const filterMonsters = monsters.filter(
    (monster) => monster.name.toLowerCase().includes(searchField)
  )
  return (
    <div className="App">
      <input
        className='search-box'
        type='search'
        placeholder='search monsters'
        onChange={onSearchChange}
      />
      {
        filterMonsters.map((monster) => {
          return (<div key={monster.id}>
            <h1>{
              monster.name
            }
            </h1>
          </div>)
        })
      }
    </div>
  );
}
```

after Optimization this class component is only going to build this function once when initializes the class for the
first time because it's a method.
Once that method is initialized, whenever render runs right now, it's just always going to refer to this method that's
already been initialized.It's not going to just renationalise an anonymous function over and over again every time
renderer gets called.

Another optimization we can make is that instead of just calling this everywhere, we can actually use the structuring in
Es6. And structuring is a big benefit for this exact reason. It makes our variables look shorter and it makes things
easier to read.

## Rendering and ReRendering

render based on two conditions:<br>

- When setState gets called and when props are updated

> react renders on mounts and rerenders whenever props change and setState gets called.

### How to Rendering and ReRendering

We saw that we initialize the app we call render from App.js and then component did Mount happens;
And then we do the fetch we call the set state again. Renderer map just happens.

So we know that setState will trigger a render from calling.However, components will also render when prompts change.

When we first render our card-list, we are getting an empty array. This is the initial state value Of monsters inside of
App.js

And then what happens is that we call set state with the full list of users in our componentdidmount;That's why we see
the second time that this array is now a full array.

I need to probably rerender in case the UI is based on our props, which is exactly what's happening.

This is why all of these are now updated because React is saying, Oh, I have new props, let me rerender the component
with the new props are props.

As we know from our code directly actually gives us the new monsters we map over the monsters, which is our props, and
that's how we see the UI update with all of these monsters.

### How to Render from top down

when it's going to attempt to render the app component first, meaning it goes to the constructor and then it calls the
render call of our app.

When it's going through a render as it goes line by line runs all of our code and then it goes into this return. And
inside here it now sees card-list. Once it sees card-list as a component, then it's going to try and run this card-ist
components different lifecycle methods. So from the cardless component, it's going to call the constructor, which even
though we haven't written it, it's running it under the hood. And then it's going to run the render and actually render
out what's inside.

If we had another component here, imagine we have a third component and we call it third component. At this point, after
running through the render and the constructor, then it's going to go into another component and it's going to do the
same thing, it's going to run this components constructor. This components render and any subsequent children are going
to do the same thing. So it's going from top down.


