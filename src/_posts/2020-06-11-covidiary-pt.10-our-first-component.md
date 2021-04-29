---
layout: post
date: 2020-06-11 21:37:41 +0000
title: COVIDiary pt. 10 - Our First Component
permalink: covidiary_pt_10_-_our_first_component
image: /images/heroes/covidiary.jpg
image_hero: /images/heroes/covidiary.jpg
rainbow_hero: true
---
Welcome to Part 10 of the COVIDiary project! If you’re just joining us or missed a post, here’s what we’ve done so far:

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

This week, we’re FINALLY writing code that will actually render in our browser! Today, we’re going to build our `Footer` component. Though it’s a relatively simple piece of our application, I decided to start with it for a few reasons. First, the `Footer` is the only page element that will be consistent throughout our entire application. It also gives us the opportunity to practice using a few tools that will be used extensively in the coming weeks. Finally, its simplicity allows us to focus on some React basics without having to worry about the more nuanced aspects.

## Stub the Component

Create a new file in your `src/components` folder called `Footer.js`. Because our component doesn’t need to hold state, we can keep it simple as a functional component. Let’s stub that out really quick:

```jsx

import React from 'react';

const Footer = () => {
	return (
		<div>
			Hello World!
		</div>
    );
};

export default Footer;
```

## Import the Footer

Let’s add our `Footer` to `App.js` so we can actually see our work in the browser.

In `src/App.js`

```jsx

import Footer from './components/Footer';
```

Just before the closing `</div>` In the `render()` section, add our component:

```jsx

<Footer />
```

In your terminal, run `yarn start`. This will open your application in the browser. Right now, it should look something like this:

![Footer with Hello World](/images/footer1.png "Footer")

## Fill in the Details

Now that we’ve got our server up and running, let’s change that “Hello World” to something we actually want, shall we? From here on out, we’re working in `components/Footer.js`

First, let’s replace the `<div>` in our `render()` with `<footer>`. Then, we’ll add our logo and copyright information:

```jsx

<footer>
  {/*Logo link to CodeWitch blog*/}
  <a href={'[http://codewitch.dev](http://codewitch.dev "http://codewitch.dev")'}
  /*Opens link in new tab*/
  target={'_blank'}
  rel={'noopener noreferrer'}>
  	<img src={'./CodeWitchLogo.png'} alt="AudTheCodeWitch Logo" height='50px' />
  </a>

  {/*Copyright information*/}
  <p>©2020 Audrea Cook</p>

</footer>
```

Let’s also add links to our social media profiles. We’ll use free icons from [fontAwesome](https://fontawesome.com/). To do this, we need to install some more packages. In your terminal, run the following:

    $ yarn add @fortawesome/fontawesome-svg-core @fortawesome/free-solid-svg-icons @fortawesome/react-fontawesome @fortawesome/free-brands-svg-icons @fortawesome/free-regular-svg-icons

When that is complete, import the icons by adding the following two lines to the top of your page:

```jsx

import { FontAwesomeIcon } from '@fortawesome/react-fontawesome'
import { faGithub, faTwitter, faLinkedin } from '@fortawesome/free-brands-svg-icons'
```

While we’re adding imports, let’s also bring in the react-bootstrap components we’ll be using:

```jsx

import ListGroup from "react-bootstrap/ListGroup";
import ListGroupItem from "react-bootstrap/ListGroupItem";
```

Now, we’re ready to add some more code to our `<footer>` element:

```jsx

{/*Using a ListGroup to create buttons for external links*/}
<ListGroup horizontal={"sm"} /*Will display horizontally vs vertically for screens size sm and up*/>
  <ListGroupItem action /*turns item into link button*/ href='https://github.com/AudTheCodeWitch' target="_blank" rel={'noopener noreferrer'} >
    {/*icon + text description*/}
    <FontAwesomeIcon icon={faGithub} /> GitHub
  </ListGroupItem>

  <ListGroupItem action href='https://twitter.com/AudTheCodeWitch' target="_blank" rel={'noopener noreferrer'} >
    <FontAwesomeIcon icon={faTwitter} /> @audTheCodeWitch
  </ListGroupItem>

  <ListGroupItem action href='https://www.linkedin.com/in/audreacook/' target="_blank" rel={'noopener noreferrer'} >
	  <FontAwesomeIcon icon={faLinkedin} /> LinkedIn
  </ListGroupItem>
</ListGroup>
```

If you save and refresh your browser, the footer should now look something like this:

![Footer with external links and logo](/images/footer2.png "Finished footer")

## Coming Up

Now that we’ve got our `Footer` component, we’re ready to keep building our application! Next week, we’ll tackle the `Header`, another component that will be shared on every page! From there, we’ll really start to bring our project to life!
