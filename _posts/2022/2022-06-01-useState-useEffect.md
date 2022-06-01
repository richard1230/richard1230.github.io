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





## build own useState
```javascript
 let isMount = true;
  let workInprogressHook = null;
  const fiber = {
    stateNode: App,
    memoizedState: null,
  }
  function useState(initialState) {
    let hook;
    if (isMount) {
      hook = {
        memoizedState: initialState,
        next: null,
        queue: {
          pending: null
        }
      }
      if (!fiber.memoizedState) { //调用第一个useState的时候走这
        fiber.memoizedState = hook;
      } else {//第二个useState
        workInprogressHook.next = hook
      }
      workInprogressHook = hook;

    } else { //update
      hook = workInprogressHook
      workInprogressHook = workInprogressHook.next
    }

    let baseState = hook.memoizedState;

    if (hook.queue.pending) {//使用useState中的setXXX更新值走这里
      let firstUpdate = hook.queue.pending.next;

      do {
        const action = firstUpdate.action;
        baseState = action(baseState);
        firstUpdate = firstUpdate.next;
      } while (firstUpdate !== hook.queue.pending.next)
      hook.queue.pending = null;
    }

    hook.memoizedState = baseState;
    return [baseState, dispatchAction.bind(null, hook.queue)]

  }

  //对应useState中的setXXX
  function dispatchAction(queue, action) {
    const update = {
      action,
      next: null
    }

    if (queue.pending === null) {//更新每一个useState的？
      //u0--> u0 ---> u0
      update.next = update;
    } else { //
      update.next = queue.pending.next;
      queue.pending.next = update;
    }
    queue.pending = update;
    schedule();
  }

  function schedule() {
    workInprogressHook = fiber.memoizedState
    const app = fiber.stateNode();//这里需要再次调用App--->再次调用useState
    console.log("app: ",app)
    isMount = false;
    return app;
  }


  function App() {
    const [num, updateNum] = useState(0);
    // debugger;
    const [num1, updateNum1] = useState(10);//每次渲染的时候这几个useState顺序一定要相同

    console.log('isMount: ', isMount)
    console.log("num: ", num)
    console.log("num1: ", num1)

    return {
      onClick() {
        updateNum(num => num + 1)
      },
      onFocus() {
        updateNum1(num => num + 10)
      }

    }
  };
  window.app = schedule();
  app.onClick();
  app.onClick();
  app.onClick();
  app.onFocus();
  app.onFocus();
```



## pure function and impure function

>函数与外界交流数据只有一个唯一渠道:
>参数和返回值。


纯函数（Pure function）:返回结果只依赖于它的参数，而且没有任何可观察的副作用;

- 给纯函数传入相同的参数，永远会返回相同的值。如果返回值依赖外部变量，则不是纯函数。

```javascript
//pure function
//纯函数  不管外部如何天翻地覆，只要传入的参数是确定的，那么值永远是可预料的
function purefuncA(a,b){
  return a+b
}
purefuncA(1,5)//6

//// 非纯函数  返回值也依赖外部变量c，结果无法预料
//impure function
let c = 3;
const funcA = (a,b)=>{
  return a+b+c
}

funcA(2,4)//9
let c = 5;

funcA(2,4)//11
```
- 一个函数在执行过程中产生了外部可观察的变化，则这个函数是有副作用(Side Effect)的。
>通俗点就是函数内部做了和运算返回值无关的事，比如修改外部作用域/全局变量、修改传入的参数、发送请求、console.log、手动修改 DOM 都属于副作用。


纯函数很严格，几乎除了计算数据什么都不能干，计算的时候还不能依赖自身参数以外的数据。


>小结:
>满足纯函数就是要满足两点:<br>
>1.函数返回结果只依赖它的参数。<br>
>2.函数执行过程中不会对外产生可观察的变化。<br>


