Server Side Rendering with Create React App
===========================================

I wanted to add server side rendering to create react app, especially after I added an api server side, based on: https://medium.com/@patriciolpezjuri/using-create-react-app-with-react-router-express-js-8fa658bf892d#.sckywa9cy

With Server Side Rendering, we want to render some basic pages, I don’t want to mess around with authenticating users or complex conditionals because I usually handle that in the Single Page App (SPA) way on the client side. This pretty much means I want to render raw html and nothing else, leave the html the way it was, but with the react ‘root’ element filled in with the route information

Included: redux, react-router

_Warning: uses react-router 3, v4 just dropped, it breaks everything its kinda annoying_

Install
-------
```bash
# Why aren't you using yarn already?
npm i -g yarn
yarn
yarn run build
yarn run start:server
```
