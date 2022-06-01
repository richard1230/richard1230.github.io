---
title: useState and useEffect
date: 01-06-2022 
categories:
- React 
tags:
- React
---

## Basic about Functional Component
>Whenever the state updates, if there's a different value for the state value as there was in the previous state then it will re render and to re render, we need to run this entire functional component.

主要有两点:

- 1.只要state和props有变化,整个函数组件就会重新渲染;
- 2.函数组件每次渲染都是独立的

## Infinite Re-rendering(I)
```jsx
function App() {
  const [count, setCount] = useState(0);

  setCount(1); // infinite loop

  return ...
}
```
If you update the state directly inside your render method or a body of a functional component, it will cause an infinite loop.

>State updates → triggers re-render → state updates → triggers re-render → …

0--->State变化-->1--->rerender--->State变化-->1(这个1和之前的那个1的内存地址不一样，由于State发生了变化就再次触发render)--->rerender--->...


## Fix
If you want to update a state only one time when the component mounts? Use useEffect with an empty array as a dependency.

```jsx
function App() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    setCount(1);
  }, [])
  

  return ...
}

```

## Infinite Re-rendering(By Incorrectly set event handlers)

```jsx
function App() {

    console.log("app is running...")
    const [n, setN] = useState(0);
    console.log(`n: ${n}`)

    return (
        <div className='App'>
            <p>{n}</p>
            <button onClick={setN(1)}>hello</button>
        </div>
        );

}

```

result:
>app is running... ---> n: 0 ---> app is running... ---> n: 1 ---> app is running... ---> n: 1 --->......

It is not the right way to set event handlers. You need to provide a function to the onClick, not the result of the function execution. By executing a function before setting a handler, you update a state inside the render, which causes an infinite loop.

## fix

```jsx
function App() {

    console.log("app is running...")
    const [n, setN] = useState(0);
    console.log(`n: ${n}`)

    return (
        <div className='App'>
            <p>{n}</p>
            <button onClick={() => setN(1)}>hello</button>
        </div>
        );

}

```

Set a function to onClick event. It is a proper way to set event handlers. This way state will only update after a click of a button and won’t cause an infinite loop.





