---
title: The Memory Plot of Javascript
date: 09-11-2020
categories:
- Javascript
tags:
- front end
---

### Execute JS code
- Preparation before execute JS code
    - Ready Work
    - Provide API: ***window/ document/ setTimeout***
    - Above code does not belong to JS itself
    - We call these code as runtime env
    - Once put JS code into the runtime env, it starts to execute JS code

### Where is the JS code running?
     Memory

### Stack and Heap
<img src="../../../../../assets/images/StackHeap.png" width="500" alt="Heap and Stack">

- Red area divided into Stack and Heap
- The data structure about a stack and heap will be talked later
- Stack: Each data stored in order
- Heap: Each data stored randomly
> Rules:
> - There are two data types: Object and non-object
> - Non-Object stores in the Stack
> - Object stores in the Heap
> - '=' operator always copy right content to left
> - Example(When the value has been changed):
    >
    >    <img src="../../../../../assets/images/Change_Value.png" width="500" alt="Change Value">
    >    <img src="../../../../../assets/images/window_picture1.png" width="500" alt="Window in memory">
    >    <img src="../../../../../assets/images/window_picture2.png" width="500" alt="Window in memory 2">

### When you need to know the structure of a function
- use ```console.dir(window.Object)```

### What the difference between \_\_proto\_\_ and prototype?
- Both of then store the address of the prototype
- However, prototype only exists in functions
- \_\_proto\_\_ exists in every new object

***Important Picture Note***
> <img src="../../../../../assets/images/Prototype_Array_Object.png" width="500" alt="Change Value">
