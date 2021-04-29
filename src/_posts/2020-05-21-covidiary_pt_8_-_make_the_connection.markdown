---
layout: post
title:      "COVIDiary pt. 8 - Make the Connection"
date:       2020-05-21 19:17:10 +0000
permalink:  covidiary_pt_8_-_make_the_connection
image: /images/heroes/covidiary.jpg
image_hero: /images/heroes/covidiary.jpg
rainbow_hero: true
---


Welcome to Part 8 of the COVIDiary project! If you’re just joining us or missed a post, here’s what we’ve done so far:



*   [Part 1: Project Introduction](https://www.codewitch.dev/covidiary_-_a_rails_react_project)
*   [Part 2: Initial Setup](https://www.codewitch.dev/covidiary_part_2_-_initial_setup)
*   [Part 3: Building the Database](https://www.codewitch.dev/covidiary_pt_3_-_building_the_database)
*   [Part 4: Frontend Setup](https://www.codewitch.dev/covidiary_pt_4_-_frontend_setup)
*   [Part 4.5: Database Fixes](https://www.codewitch.dev/covidiary_pt_4_5_-_database_fixes)
*   [Part 5: Backend Routing](https://www.codewitch.dev/covidiary_pt_5_-_backend_routing)
*   [Part 6: Formatting Data](https://www.codewitch.dev/covidiary_pt_6_-_formatting_data)
*   [Part 7: A Little More Action](https://www.codewitch.dev/covidiary_pt_7_-_a_little_more_action)

This week, we’re going to shift focus to the front end. By the end of today, we will be able to retrieve data from our API!

Before we write any code, make sure your backend server is running. In `CD-api`, run `rails s` to fire it up. Leave that running and open your `CD-Client` repository in another window.


## Write Fetch Requests

We’ll be working solely in `/src/App.js` today. We will write two separate, but extremely similar, fetch requests. Write your code in the `App` class but before the `render()` method.

```javascript

// test fetch

  // the fetch requests will run when the App.js component mounts

  componentDidMount() {

    // fetch all the public entries

    fetch('http://localhost:3000/api/entries')

      // take the response and convert it to json

      .then(response => response.json())

      // take the resulting json and log it to the console

      .then(data => {

        console.log("All public entries:", data);

      })

      // if there is an error, log an error message to the console

      .catch((error) => {

        console.error('Public Entries Error:', error);

      });

    

    // fetch the first user's entries
		
    fetch('http://localhost:3000/api/users/1/entries')

      .then(response => response.json())

      .then(data => {

        console.log("single user's entries:", data);

      })

      .catch((error) => {

        console.error('Single User Entries Error:', error);

      });

  }

```

We can now test our connection to our backend server! Start your server using `yarn start` and open it in the browser. Open the browser console so you can see the fetch results!

<center>
<img alt="Rocket Power - It worked" src="https://media.giphy.com/media/xT1R9XQAtJN7SIrSjC/giphy.gif">
</center>


## Coming Up

Eureka! The front and back ends are communicating with one another! Next week, we’ll shift our focus to building out the front end so we can actually see something.

