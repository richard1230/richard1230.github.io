---
title: React Render Flow and simple search bar
date: 06-03-2022 
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

- regardless of whether this is React or JavaScript, classes will always run the constructor function first inside of here.

- The render runs next, and what it does is the render determines what to show. This you can see kind of as the template of the HTML, so this dictates what the UI for this component  is going to be.

- Then the next life cycle that runs is componentDidMount, I run the constructor of initialize the state, the initial state at the very least, and I am going to now render the initial UI of this component. So it's actually going to mount this initial UI onto the Dom.
 what this means is that whatever the initial state of your component is, is what it will mount on.
 And here we are fetching some JSON.
This is asynchronous, so we actually don't know when this data is going to come back.
Once it comes back, we are going to now update the state.
But the moment that that state updates remember,  the moment state changes and you've called set state.

- call the render again

### summary
Run the constructor, run the initial render when your initial monster's value was an empty array.

Then, once your component mounts fetch, the new users call that state and once again, once the state gets called Call Render Again and now Component is the new updated users list.

- constructor runs first, initialize your state,

- render your initial component UI.

- Then once you need some API, calls to it in the component at Mount lifecycle. Once that happens, you want to set state to make sure that your component updates.

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