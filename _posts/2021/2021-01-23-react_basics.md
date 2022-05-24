---
title: React Basics
date: 23-01-2021
categories:
- React
tags:
- front end
---

### package.json

```"react-scripts":"3.0.0"``` =>  It allows use to have no worry about webpack and babble.

 ```javascript
    "scripts": {
    "start": "react-scripts start",
    // starts the react project by running "yarn start"
    "build": "react-scripts build",
    // it used to turn all of the react code in the <source> folder into that version the browser to understand and put it inside of this <public> folder,
    // after running "npm run build" generated a <build> folder, this is the place ready to be deployed and be displayed to the outside users.
    "test": "react-scripts test",
    // run the test code we will going to write
    "eject": "react-scripts eject"
    // take out all of the configuration files that it's hidden from us from Babble and webpack in case wwe will manage it ourselves.
    }
  ```

### 'source' folder
- All applications live, our workspace

### 'public' folder
- The browser needs an older version of javascript and html to understand

### 'class' vs. 'className'
- ```javascript
    // class
     class App extends Component {
        constructor(){
           super();
          this.state = {
          string: "Hello Today I start to learn something from yihua's teaching"
        }
      }
      render(){
        return(
          // className
          <div className="App">
          <header className="App-header">
          </header>
          </div>)
      }
      //the 'className' in the render is used to differentiate the class at the beginning
  ```
  
### 'render()' method
- ```render()``` is one of the built-in methods of ```React.Component```, the ``` super()``` inside the React.Component's ```constructor()``` helps us call ```render()```

### Two Ways to create components
- Class Component
- Functional Component

### 'props' in the functional component
- ```javascript
      import React from 'react';
        export const CardList = (props)=>{
          console.log(props);
          return (<div>hello</div>)
        }

        // App.js
        // ...
        render() {
          return (
            <div className="App">
              <CardList name="Grace-Yueran"/>
              {
                this.state.monsters.map(item =><h1 key={item.id}>{item.name}</h1>)
              }
            </div>
        )
      }
    ```
    - ```props``` is going to be an object of any properties that you write onto this component where it gets used.

### 'children' Property
```javascript
    // card-list.component.jsx
    import React from 'react';
        export const CardList = (props)=>{
          console.log(props);
          return (<div> {props.children}</div>)
    
    // App.js
      render(){
          return (
          <div className="App">
            <CardList name="Grace-Yueran">
    
          // children property
            <h1>Grace Yueran</h1>
            </CardList>
            {this.state.monsters.map(item => <h1 key={item.id}>{item.name}</h1>) }
          </div>
        )
      }
 ```
- ```Children``` are actually what you pass in between the brackets of our component that gets called.

### The Benefits of When do we break things down into components?
- To be a great React developer you need to be good at these very well:
    1. Decide on Components
    2. Decide the State and where it lives
    3. What changes when state changes
- By breaking things down we're making things more flexible because each component does one thing and one thing really well.
- It can be used in other places, the bigger a file gets the more JSX we have, the more logic we have, the harder it gets to be used in another place.
- The KEY here is that the reason we break things down into smaller components is that we combine each component with its concern and that concern is that this component is only concerned about card list. This component is only concerned about cards.

### The second argument of 'setState()'
```javascript
    // App.js
    // if we wanted to see or do something with our state right after we set it
    // then we have to do it inside of this second argument function that will get called right after the set state.
    render() {
        return (
            <div className="App">
              <input type='search' placeholder='Search Monster'
                    onChange={e => this.setState({searchField: e.target.value}, () => {
                      console.log(this.state)
                    })}/>
              <CardList monsters={this.state.monsters}/>
            </div>
        )
      }
```
- **The second parameter** to ***setState()*** is an optional callback function that will be executed once ***setState*** is completed and the component is re-rendered. ***componentDitUpdate*** should be used instead to apply such logic in most cases.

### Destructuring
```javascript
      constructor(props) {
      super(props);
      this.state = {
        monsters: [],
        searchField: ''
      }
    }

  // the state object is what we want to pull the properties of
  const {monsters, searchField} = this.state
  // equals
  const monsters = this.state.monsters
  const searchField = this.state.searchField
```
 
### When use class component and when use functional component?
- ***functional components***, unlike ***class components***, they don't have the access to ***state***, because they don't have the access to constructor, which is a class method on our ***Component*** that we import from our React, that we extend our class from.
- They also don't have access to lifecycle methods, because we don't always need lifecycle methods or internal state.
- Sometimes we only want to render some HTML, that's what functional component really is.
- A functional component is just a component that gets some props and returns some HTML.
- If you don't need internal state nor lifecycle methods, then just use functional components. It's easier to read and easier to test.

### The test of the scope of arrow function
 ```javascript
   // ======= define the function in the window scope
     const myFunc = () => console.log(this)
     // call myFunc()
     myFunc()
     // result: Window {window: Window, self: Window, document: document, name: "", location: Location, …}


    // ======= define a function in a class scope
    class FatherClass{
        myFunc2 = () => console.log(this)
        }
      let obj = new FatherClass()
      obj.myFunc2()
      // result: FatherClass {myFunc2: ƒ}
 ```

### Always use the Latest Version of React and ReactDOM
```javascript
    {
    "name": "monsters-rolodex",
    "version": "0.1.0",
    "private": true,
    "homepage": "https://www.graceyutech.com/monsters-rolodex/",
    "dependencies": {
      "@testing-library/jest-dom": "^5.11.4",
      "@testing-library/react": "^11.1.0",
      "@testing-library/user-event": "^12.1.10",
      "gh-pages": "^3.1.0",
      "react": "^17.0.1",
      /* '^' symbol means whatever the package manager you are using
      wheather it is a yarn or NPM, whenever it sees npm upgrade or yarn upgrade,
      to update to the latest stable non-breaking version.
      In other words, it should be at least using the '17.0.1' version or greater of react-dom and react.
      */
      "react-dom": "^17.0.1",
      "react-scripts": "4.0.3",
      "web-vitals": "^1.0.1"
    }
```

- What is the ```yarn.lock``` file?
    1. It isn't auto-generated file by either NPM or a yarn that locks the version of all the packages inside of our application within a specific range based on the rules that we set inside of package.
    2. Without ```'^'``` this Caret symbol, the ```yarn.lock``` file, the version of React and ReactDOM and React scripts are locked exactly that version, the fixed version shows in ```package.json``` file.
    3. However, when we added this caret ```'^'```, it gives more flexibility which means the ```yarn.lock``` file is out of date and needs to be updated. And this file only updates whenever you run ```yarn install```.

- And why we need this file?
    1. If there are multiple people are working on this application they are all using versions of dependencies that don't conflict with each other, because maybe some people are running React '17.0.0' someone is running React '16.0.0.', and there is difference in features that might be breaking in the application.
    2. So ```yarn.lock``` file just ensures everybody is using a consistent version of these dependencies.
    3. After we run ```yarn.lock``` file, we generated a new lock file. From now on, you can simply run your yarn upgrade whenever you want to upgrade these dependencies.


### One main difference between ***yarn*** and ***npm***
- This command ```npm audit fix``` will go through and update the versions to a version of a package where it doesn't have a security concern anymore.
- While, yarn doesn't have this command, we only can install and upgrade all the packages that you see with a vulnerability.

### What is Virtual DOM?
- Virtual DOM is a javascript object. It's a way to emulate the Real DOM.

### State updates are asynchronous!!! You should Pass a function as the first parameter in the setState() to update the state synchronously!!!

### React Concepts
 1. Don't touch the DOM. I'll do it
 2. Build websites like lego blocks
 3. Unidirectional data flow
 4. UI, The rest is up to you

### The job of a SENIOR React Developer
1.Decide on Components
2. Decide the State and where it lives
3. What changes when state changes
4. ***This idea of deciding on components, deciding about the state and where it lists what happens when state changes because of user action. These all things that nobody is going  to tell you. These are things that is dependent on each app that you built.***
5. ***What the senior developers have had this ability to think for themselves not just follow a tutorial but actually implement these things based on knowledge and experience that they've gathered.***

### The Benefit of using Arrow Function in JSX!!!
> ```this``` keyword with arrow function points to the current class object ```NameForm``` . However, without arrow function, you should manually bind the methods to current class object ```NameForm```. Otherwise, ```this``` will point to global object ```window```. Therefore, we can downsize the code by using arrow function.

#### Example 1:

```javascript
// Code without Arrow function
class NameForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {value: ''};
    // you need to manually bind the methods to the current class object
    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('A name was submitted: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input type="text" value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```

#### Example 2:

```javascript
// Code with Arrow function
class NameForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {value: ''};
  }

  handleChange = event => {
    this.setState({value: event.target.value});
  }

  handleSubmit = event => {
    alert('A name was submitted: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input type="text" value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```



