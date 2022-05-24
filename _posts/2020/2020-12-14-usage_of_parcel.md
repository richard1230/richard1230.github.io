---
title: Usage of Parcel
date: 14-12-2020
categories:
- Server
tags:
- front end
---

```javascript
  1. rm -rf dist // this is clear the dist if you want to build a brand new parcel of your code
  2. parcel build src/index.html --no-minify --public-url ./

  https://yueran-yu.github.io/JRG-Course/NavigationPage/dist/

  //this path that will show for user to click

  // The complete Parcel command
  parcel --help // look into the document parcel

  // add absolute path
  parcel build src/index.html --no-minify --public-url  https://yueran-yu.github.io/JRG-Course/NavigationPage/dist/

  // add relative path
  parcel build src/index.html --no-minify --public-url ./

  // create a /gitignore file to ignore .idea and node_modules/
  3. .gitignore
  ```
> You also can add the the ```Parcel``` command into the ```package.json``` file
  ```javascript
      "scripts": {
      "build": "rm -rf dist; parcel build src/index.html --no-minify ./"
      // here is the sentence you need to add to;  window system may not support ';' after 'dist'
      },
      "devDependencies": {
        "cssnano": "^4.1.10"
      },
      "name": "NavigationPage",
      "version": "1.0.0",
      "main": "index.js",
      "license": "MIT"
      }
  ```
> You can run the ```Parcel``` next time by typing **```yarn build```** in the terminal

[My Website Link: Front-End Navigation](https://yueran-yu.github.io/JRG-Course/NavigationPage/dist/index.html)

