---
title: Controlled Component VS. Uncontrolled Component
date: 13-06-2021
categories:
- React
tags:
- front end
---


- Reference Article:
    - [1. Controlled Component](https://stackoverflow.com/questions/42522515/what-are-react-controlled-components-and-uncontrolled-components)
    - [2. Controlled and uncontrolled form inputs in React don't have to be complicated](https://goshakkk.name/controlled-vs-uncontrolled-inputs-react/#conclusion)


- A *Controlled Component* is one that takes its current value through **props** and notifies changes through callback like ***onChange*** A parent component "controls" it by handling the callback and managing its own state and passing the new values as props to the controlled component. You could also call this a "dumb component".
  &
- A *Uncontrolled Component* is one that stores its own state internally, and you query the DOM using a **ref** to find its current value when you need it. This is a bit more like traditional HTML.

```javascript
   // Controlled:
   <Input type='text' value={value} onChange={handleChange}/>

   //Uncontrolled:
  <Input type="text" defaultValue="foo" ref={inputRef} />
   // Use `inputRef.current.value` to read the current value of <input>
```


