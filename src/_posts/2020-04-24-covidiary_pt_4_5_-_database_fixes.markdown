---
layout: post
title:      "COVIDiary pt. 4.5 - Database Fixes"
date:       2020-04-24 16:21:20 +0000
permalink:  covidiary_pt_4_5_-_database_fixes
image: /images/heroes/covidiary.jpg
image_hero: /images/heroes/covidiary.jpg
rainbow_hero: true
---


<center>
<img alt="Cool Cats and Kittens" src="https://media.giphy.com/media/RGixkYkOKdWATSReHt/source.gif">
</center>

Welcome to Part 4.5 of the COVIDiary project! If you’re just joining us or missed a post, here’s what we’ve done so far:



*   [Part 1: Project Introduction](https://www.codewitch.dev/covidiary_-_a_rails_react_project)
*   [Part 2: Initial Setup](https://www.codewitch.dev/covidiary_part_2_-_initial_setup)
*   [Part 3: Building the Database](https://www.codewitch.dev/covidiary_pt_3_-_building_the_database)
*   [Part 4: Frontend Setup](https://www.codewitch.dev/covidiary_pt_4_-_frontend_setup)

This week, we’re going to work on our PostgreSQL database in the `CD-api` directory. By the end of today, we will:



1. Fix improper boolean names
2. Add is_public boolean to entries
3. Update seed file
4. Reset database


## Ch-ch-ch-CHANGES

I was reading up on naming conventions this week, and I came across [this article](https://dev.to/michi/tips-on-naming-boolean-variables-cleaner-code-35ig). I realized the boolean names in our tables did not follow best practices, and I set about changing them.

<center>
<img alt="Good Idea at the Time" src="https://media.giphy.com/media/gKGzjtXVrVPIsgbREz/source.gif">
</center>

I’m going to go into Part 3 and fix the mistakes I made. If you’ve been coding along with me, check out the video below to see how to make the changes yourself!

<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/MVqeF7RTjAk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>


## Coming Up

Next week, we’ll work on setting up our routes, serializers, and controllers so the front and back ends can talk to one another. Until then, stay well!

<center>
<img alt="Stay Home" src="https://media.giphy.com/media/lQ701BEcCllM2BOQpR/source.gif">
</center>
