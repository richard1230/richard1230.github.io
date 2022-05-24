---
title: How to Write Extensible Code 
date: 16-03-2021 
categories:
- Coding Rules 
tags:
- learning
---

#### Are you starting to feel like we're doing a lot of things over and over the same way we're creating reducers and actions and selectors and connecting components and rendering components and if things seem repetitive to you, that's actually a good thing because what we're doing is we're making things very simple.

>

#### Now we're creating a lot of files in our project but these files are all usually under one hundred lines of code. Each file is very very simple isn't it. We haven't run any crazy long thousand line algorithms. Everything is nice small and simple. And if you notice, each one makes each component very very small and also very extensible. That is he reuses components and features across the application so that he's not constantly doing the same thing over and over.

>

#### It's ok if we're copying code that is well similar in let's say a selector or using map state to props over and over. The idea is that he's structured the project in such a way that your eye could come to the project and really easily add features, really easily add a custom button or a cart item. And this is a sign of a really good developer. Because when he's coding, he is coding for the future as well.

>

#### He knows that by thinking a little bit about how to make the code more extensible. In the future he will benefit as he takes on more and more features because he can use the same functionality in one part of the app and in another part of the app.

>

#### React and Redux really allows us to create extensible code and the other word that you might be thinking of is also predictable code.