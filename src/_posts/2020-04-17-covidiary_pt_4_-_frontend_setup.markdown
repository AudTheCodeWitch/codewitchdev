---
layout: post
title:      "COVIDiary pt. 4 - Frontend Setup"
date:       2020-04-17 22:11:46 +0000
permalink:  covidiary_pt_4_-_frontend_setup
image: /images/heroes/covidiary.jpg
image_hero: /images/heroes/covidiary.jpg
rainbow_hero: true
---


Welcome to Week 4 of the COVIDiary project! If you’re just joining us or missed a post, here’s what we’ve done so far:

*   [Part 1: Project Introduction](https://www.codewitch.dev/covidiary_-_a_rails_react_project)
*   [Part 2: Initial Setup](https://www.codewitch.dev/covidiary_part_2_-_initial_setup)
*   [Part 3: Building the Database](https://www.codewitch.dev/covidiary_pt_3_-_building_the_database)

This week, our focus will be on the front end. All work will be completed in the COVIDiary-client repository. By the end of today, we will:

*   Create our React app
*   Install packages we’ll need later down the road
*   Create our store


## 1. Create the React app

For our front end, we are building a Single-Page Application. Our buddies at Facebook make it really easy to set up your initial development environment using Create React App. You can read more about it [here](https://github.com/facebook/create-react-app).

In your terminal, make sure you are in the `/CD-client` directory. Then, enter the following command:

```

yarn create react-app client

```

Similar to when we built our Rails API, this step might take a minute. Patience, grasshopper.


## 2. Install additional packages

We’re going to add a few things right off the bat so they will be there when we’re ready for them down the road.


### Bootstrap

```

yarn add react-bootstrap bootstrap

```

Because we used Create React App, we need to do a little configuring upfront in order to customize Bootstrap later on. Follow the instructions under “Using a Custom Theme” [here](https://create-react-app.dev/docs/adding-bootstrap/), and you’ll be good to go.


### React-Router-Dom

```

yarn add react-router-dom

```

In `src/index.js`:

```javascript

import { Router } from 'react-router-dom'

```


### Redux and Thunk

```

yarn add redux react-redux redux-thunk

```

In `src/index.js`:

```javascript

import { createStore, applyMiddleware, compose } from 'redux';

import thunk from 'redux-thunk';

import { Provider } from 'react-redux';

```

<center>
<img alt="Thunk" src="https://media.giphy.com/media/mclaz3NEq6en6/source.gif">
</center>


## 3. Create the store

We’re using Redux to manage the state of our application. First, we need to create a store in `src/index.js`.

```javascript

const composeEnhancers = window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__ || compose;

// Create store

// Use applyMiddleware to enable thunk

let store = createStore(userReducer, composeEnhancers(applyMiddleware(thunk)));

```

In the `render()` section, we need to wrap `<App />` in `<Provider />` so our components can access the store we just created.

```javascript

ReactDOM.render(

   {/*Wrap entire app in provider to give all components access to the store*/}

    <Provider store={store}>

        <App />

    </Provider>,

  document.getElementById('root')

);

```

If we spun up our app right now, we’d get an error. 

<center>
<img alt="Failed to compile" src="https://i.imgur.com/Z9LuGSH.jpg">
</center>

That’s because we haven’t created our `userReducer` yet. Let’s do that now. Create a new directory in `/src` called `reducers`. In that directory, we’ll create our `userReducer.js` file.

In `src/reducers/userReducer.js`, let’s stub out our reducer function. We’ll worry about building it up later.

```javascript

export default function userReducer(state = {users: []}, action) {

    return state

}

```

Let’s import our new reducer in `src/index.js`

```javascript

import userReducer from './reducers/userReducer'

```

Now, if you spin up the app with `yarn start`, you should see something like this:

<center>
<img alt="React Success!" src="https://i.imgur.com/IC6bVnb.jpg">
</center>

Success!


## Coming Up

We now have the beginnings of a spectacular application. Next week, we’ll start connecting the front and back end! I know I said we’d get to user authentication this week, but I decided to break this post into a few smaller, (hopefully) more organized chunks. We’ll get there soon, I promise!

