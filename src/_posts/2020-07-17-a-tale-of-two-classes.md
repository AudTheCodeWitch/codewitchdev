---
layout: post
date: 2020-07-17 11:06:31 -0600
title: A Tale of Two Classes
permalink: a_tale_of_two_classes
image: /images/heroes/two_classes.jpg
image_hero: /images/heroes/two_classes.jpg
rainbow_hero: true
---
Yesterday, I was challenged by a potential employer (fingers crossed) to share a few JS classes I'm proud of. I had a lot of fun writing this up, and I figured I would share it with y'all, as well.

Below, you will find code samples from my React app, [OurCal](https://github.com/AudTheCodeWitch/OurCAL), which is deployed on Heroku, [here](https://our-cal.herokuapp.com/). I chose this project because it was originally written in vanilla JS before I refactored it, and I thought it would be interesting to show how the classes evolved.

The [vanilla JS `Block` class](https://github.com/AudTheCodeWitch/OurCAL/blob/v0.1.0/frontend/javascripts/block.js) creates the 25x25 pixel grid, or block. The constructor accepts the block’s `name` and an array of `pixels`. To create the individual `Pixel` objects, the constructor calls the `createPixels` method, which loops through the `pixels` array and calls on the `Pixel` class for each element. This method returns the newly-created `Pixel` objects as an array to be sent to the back end.

The [vanilla JS `Pixel` class](http://github.com/AudTheCodeWitch/OurCAL/blob/v0.1.0/frontend/javascripts/pixel.js) is a simple constructor. It accepts four arguments, the `x` and `y` coordinates, the background `color`, and the `color_variable` representing the pen used to select the pixel.

After converting OurCal to a React app, the classes get a bit more complex (and fun).

<center>
<img src='https://media.giphy.com/media/42wakmA8VzrB7eP0VT/source.gif' alt='Moira Rose saying, "No one will ever accuse you of being vanilla again."'>
</center>

The [React `CompleteBlock` class](https://github.com/AudTheCodeWitch/OurCAL/blob/main/client/src/components/CompleteBlock.js) displays a fully-colored block. It takes the block’s `name` and `block` data as props. The `createBlock` and `createColumns` methods work in tandem to populate a grid with individual `Pixel` objects. On `componentDidMount()`, the pixels are then filled with the appropriate background colors, using the `colorPixels` method.

The [React `Pixel` class](https://github.com/AudTheCodeWitch/OurCAL/blob/main/client/src/components/Pixel.js) creates the individual pixels, based on the block’s location, which is passed in through props. If the location is `Template` (the editable block), a click handler is attached to the pixel. The `handleClick` method toggles the pixel’s `className` (and corresponding background color). Pixels in the `Template` location are also added to the Redux store through `componentDidMount.`

## Bug Alert!

The current Heroku deployment contains a bug dealing with the toggled background colors.

<center>
<img src='https://media.giphy.com/media/1xOQlQxrIX4Jw6lBZI/giphy.gif' alt='Night Flight bug and screaming woman'>
</center>

I am aware of it and have addressed the problem in the code. I'm working on deploying the fix, hopefully, later today.
