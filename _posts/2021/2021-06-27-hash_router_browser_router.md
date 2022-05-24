---
title: Hash Router VS. Browser Router
date: 27-06-2021
categories:
- React Router
tags:
- front end
---


### HashRouter
- It uses URL hash, it puts no limitations on supported browsers or web server. Server-side routing is independent from client-side routing.

- Backward-compatible single-page application can use it as example.com/#/react/route. The setup cannot be backed up by server-side rendering because it's / path that is served on server side, #/react/route URL hash cannot be read from server side. On client side, window.location.hash is parsed by React router. React router renders a component that it was configured to render for /react/route, similarly to BrowserRouter.

- Most importantly, HashRouter use cases aren't limited to SPA. A website may have legacy or search engine-friendly server-side routing, while React application may be a widget that maintains its state in URL like example.com/server/side/route#/react/route. Some page that contains React application is served on server side for /server/side/route, then on client side React router renders a component that it was configured to render for /react/route, similarly to previous scenario.

- HashRouter basically it uses the hash in the URL to render the component.

### BrowserRouter
- BrowserRouter, it uses HTML5 history API to render the component.It uses history API, i.e. it's unavailable for legacy browsers (IE 9 and lower and contemporaries). Client-side React application is able to maintain clean routes like example.com/react/route but needs to be backed by web server. Usually this means that web server should be configured for single-page application, i.e. same index.html is served for /react/route path or any other route on server side. On client side, window.location.pathname is parsed by React router. React router renders a component that it was configured to render for /react/route.

- Additionally, the setup may involve server-side rendering, index.html may contain rendered components or data that are specific to current route.


[Resource: What the difference between hash router and browser router](https://stackoverflow.com/questions/51974369/what-is-the-difference-between-hashrouter-and-browserrouter-in-react)
