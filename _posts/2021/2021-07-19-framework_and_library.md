---
title: The Difference Between a Framework and Library 
date: 19-07-2021 
categories:
- React 
tags:
- front end
---

### What the difference between framework and library?

- Both libraries and frameworks are reusable code written by someone else. Their purpose is to help you solve common
  problems in easier ways.

- #### The Technical Difference

The technical difference between a framework and library lies in a term called inversion of control. When you use a
library, you are in charge of the application flow. You choose when and where to call the library. When you use a
framework, the framework is in charge of the flow. It provides you with a few places to plug in your code, but it calls
the code you plugged in as needed.

 <img src="../../../../../assets/images/frameworkvslibraries.png" width="800" alt="frameworks vs libraries">

- You tell libraries what to do, frameworks tell you what to do.

#### One definition I know is:

- a framework is a software where you plug your code into
- a library is a software that you plug into your code


### Why is React a library and not a framework?

- React itself does not include many of the React-specific libraries you're going to need for most projects. Angular and
  Vue, by comparison, include many more tools all bundled within the core package itself.
- Many developers consider this discussion of what is and isn't a library to be trivial. But it has real consequences
  for our development process. In other words, because React is a library and not a framework, becoming a skilled React
  developer entails having a good knowledge of third-party React libraries.
    - The Third-Party React libraries example:
    - Redux, Redux Form, React Router, Styled Component

### Since React is a library, you must choose the tools on your own

- That means, in order to build complete React applications, you will need to choose these packages and tools on your
  own.
- For a form library, I have to decide whether I want to use the package React Hook Form or Formik. These are both
  React-specific form libraries to add important features to our forms like validation.
- For testing my React application, I might use either React Testing Library, Jest, or some combination of the two.
- For making network requests, I might need to choose between the Fetch API and Axios. I might also need to decide if I
  want to add an additional library to make managing my server state easier, such as React Query or SWR.

[3 Reference: Is React a framework or library? - Everything you need to know ](https://digitalya.co/blog/is-react-a-framework-or-library/)

- When choosing the right libraries and frameworks to build your mobile app or we app, it
- s important that a framework is popular so that it has a well-established dev community around it. If you were to
  search on google or StackOverflow a question regarding some specific functionality or bug inside the framework, you'd
  most likely want to see other people who might have encountered the issue and found a solution.

### Resource Reference: 
[1 What is the Difference Between a Framework and Library?](https://sofienebk.medium.com/what-is-the-difference-between-a-framework-and-library-2b712a1a1c41)

[2 Libraries vs. Frameworks — What’s the Difference?](https://betterprogramming.pub/libraries-vs-frameworks-whats-the-difference-5f28c53dcffe)

[3 Is React a Library or a Framework? Here's Why it Matters](https://www.freecodecamp.org/news/is-react-a-library-or-a-framework/)
