Server Side Rendering with Create React App
===========================================

I wanted to add server side rendering to create react app, especially after I added an api server side, based on: https://medium.com/@patriciolpezjuri/using-create-react-app-with-react-router-express-js-8fa658bf892d#.sckywa9cy

Included: redux, react-router

_Warning: uses react-router 3, v4 just dropped, it breaks everything its kinda annoying_


Server-Side Rendering
---------------------
The basic requirement of SSR is to handle user requests when they first land on our site. It also facilitates SEO services for a website. Compared to Client-Side Rendering it is slow as it renders once the complete requested HTML is received.

Redux
-----
Using Redux with SSR is a good choice but it requires your app's state to be sent with the response. This respopnse further is used by the client as the initial state. This is required to keep the sync between client and server as when the client needs to render the data, it needs to follow the same markup as the server else a fresh data load is required again.

Steps to pass data down to the client on SSR
-   On every request an intance to a new Redux Store is created which possibly contains some actions to be dispatched.
-   After this the state is pulled out from the store and passed down to the client for further actions.

Hence, Redux in SSR only provides a state to our App, known as the initial state.

React-Router Config
-------------------
In this example the App gets its config from react-router which contains the address of the pages to traverse once they are clicked.

Example
-------
```bash
import React from 'react'
import { Router, Route, IndexRoute, browserHistory } from 'react-router'

import App from './containers/App'
import FirstPage from './containers/FirstPage'
import SecondPage from './containers/SecondPage'
import NoMatch from './components/NoMatch'

const Routes = props => {
  return (
    <Router history={browserHistory}>
      <Route path="/" component={App}>
        <IndexRoute component={FirstPage}/>
        <Route path="second" component={SecondPage}/>
        <Route path="*" component={NoMatch}/>
      </Route>
    </Router>
  )
}

export default Routes
```

UI pages
--------
-   First Page
-   Second Page

First Page
```bash
class FirstPage extends Component {
  render() {
    return (
      <div className='bold'>
        <p>
          First Page
        </p>
        <p>{'Email: ' + this.props.user.email}</p>
        <Link to={'/second'}>Second</Link>
      </div>
    )
  }
}
```

Second Page
```bash
class SecondPage extends Component {
  render() {
    return (
      <div className='bold'>
        <p>
          Second Page
        </p>
        <Link to={'/'}>First</Link>
      </div>
    )
  }
}
```

Setting Up
----------
clone the repo either using SSH key or HTTPS
```bash

SSH
-   git clone git@github.com:chandanky23/react-server-rendered.git [optional folder name]

HTTPS
-   git clone https://github.com/chandanky23/react-server-rendered.git [optional folder name]

```

Install
-------
```bash
# Why aren't you using yarn already?
npm i -g yarn
yarn
yarn run build or yarn build
yarn run start:server or yarn start:server

Note - run is not mandatory

```