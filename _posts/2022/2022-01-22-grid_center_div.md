---
title: Center Div in the Grid 
date: 22-01-2022 
categories:
- CSS 
tags:
- CSS
---

### This is driving me crazy~! So here is the code snippet will often use in the future.

- The first style

```css
div {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    justify-items: center;
    align-content: center;
}

```

- The second style

```css
div {
    margin-top: 5vh;
    display: grid;
    height: 57vh;
    grid-template-columns: 1fr;
    grid-template-rows: 1fr 1fr;
    gap: 10px;
    justify-content: center;
    align-items: center;
}
```