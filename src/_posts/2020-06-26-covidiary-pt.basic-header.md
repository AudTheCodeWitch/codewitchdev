---
layout: post
date: 2020-06-26 15:29:46 -0600
title: COVIDiary pt. 11 - Basic Header
permalink: covidiary_pt_11_-_basic_header
image: /images/heroes/covidiary.jpg
image_hero: /images/heroes/covidiary.jpg
rainbow_hero: true
---
Welcome to Part 11 of the COVIDiary project! If you’re just joining us or missed a post, here’s what we’ve done so far:

* [Part 1: Project Introduction](https://www.codewitch.dev/covidiary_-_a_rails_react_project)
* [Part 2: Initial Setup](https://www.codewitch.dev/covidiary_part_2_-_initial_setup)
* [Part 3: Building the Database](https://www.codewitch.dev/covidiary_pt_3_-_building_the_database)
* [Part 4: Frontend Setup](https://www.codewitch.dev/covidiary_pt_4_-_frontend_setup)
* [Part 4.5: Database Fixes](https://www.codewitch.dev/covidiary_pt_4_5_-_database_fixes)
* [Part 5: Backend Routing](https://www.codewitch.dev/covidiary_pt_5_-_backend_routing)
* [Part 6: Formatting Data](https://www.codewitch.dev/covidiary_pt_6_-_formatting_data)
* [Part 7: A Little More Action](https://www.codewitch.dev/covidiary_pt_7_-_a_little_more_action)
* [Part 8: Make the Connection](https://www.codewitch.dev/covidiary_pt_8_-_make_the_connection)
* [Part 9: UX Design](https://www.codewitch.dev/covidiary_pt_9_-_ux_design)
* [Part 10: Our First Component](https://www.codewitch.dev/covidiary_pt_10_-_our_first_component)

This week, we’re creating a simple `Header` component. We aren’t getting into the nitty-gritty of adding auth just yet. Today’s goal is to get the basic layout of our `Header`. Before we begin, run `yarn start` in your terminal to open your application in the browser.

## Stub the Component

Create a new file in your `src/components` folder called `Header.js`. Add a simple functional component.

```jsx
import React from 'react';

const Header = () => {
  return (
    <div>
      COVIDiary
    </div>
  );
};

export default Header;
```

## Import the Header

Let’s add our `Header` to `App.js`.

In `src/App.js`:

```jsx
import Header from './components/Header';
```

Just after the opening `<div>` In the `render()` section, add our component:

```jsx
<Header />
```

You can remove all the default React code if you’d like. I moved it into a `main` tag so I had a placeholder between my header and footer.

```jsx

<main>
  <img src={logo} className="App-logo" alt="logo" />
  <p>
    Edit <code>src/App.js</code> and save to reload.
  </p>
  <a className="App-link" href="https://reactjs.org" target="_blank" rel="noopener noreferrer">
    Learn React
  </a>
</main>
```

Right now, your project will look something like this:

![COVIDiary with the stubbed header component](/images/basic-header.jpg "Basic Header")

## Fill in the Details

Let’s start to format our header to match our wireframe sketch. From here on out, we’re working in `components/Header.js`.

For our header, we will be using React-Bootstrap’s [`NavBar`](https://react-bootstrap.github.io/components/navbar/ "NavBar") and [`Nav`](https://react-bootstrap.github.io/components/navs/ "Navs") components. To begin, import the components at the top of your file:

```jsx
import Navbar from "react-bootstrap/Navbar";
import Nav from "react-bootstrap/Nav";
```

Now, let's replace our `div` with `NavBar`. We'll pass it props to adjust the styling.

```jsx
<Navbar expand='md' bg='dark' variant='dark' as='header'>
  {/*expand - breakpoint at which hamburger menu expands*/}
  {/*bg - sets background color*/}
  {/*variant - use dark color scheme for dark bg*/}
  {/*as - converts default <div> tag to <header> tag*/}
</Navbar>
```

Within our `Navbar`, let's put our site's name on the left. You could also use a logo here, if you had one. We'll have this element link to our root page.

```jsx
  <Navbar.Brand href="/">COVIDiary</Navbar.Brand>
```

We also want to make sure our `Navbar` is responsive so it will adapt when users adjust their screen sizes.

```jsx
<Navbar.Toggle aria-controls="responsive-navbar-nav"/>
```

Finally, let's add the main navigation links. We want them to collapse into a hamburger menu on smaller screens, so we will wrap them in a `<Navbar.Collapse>` component. Note the id and className come straight from the React-Bootstrap documentation.

```jsx
<Navbar.Collapse id="responsive-navbar-nav">
  <Nav className="ml-auto" as='nav'>
  {/*ml-auto - aligns nav links to the right of the container*/}
    <Nav.Link href="/about">About</Nav.Link>
    <Nav.Link href="/register">Register</Nav.Link>
  </Nav>
</Navbar.Collapse>
```

Our basic header is complete! Here it is on medium and larger screens:

![Header on medium and larger screens](/images/medium-header.jpg "Medium Header")

Here is the hamburger menu on small screens:

![Header with hamburger menu](/images/collapsed-header.jpg "Small Header")

And here is the expanded hamburger menu:

![Header with expanded hamburger menu](/images/expanded-small-header.jpg "Expanded Small Header")

## Coming Up

Now that we’ve got our `Header` component, we’re ready to get into some more complicated aspects of our front end!
