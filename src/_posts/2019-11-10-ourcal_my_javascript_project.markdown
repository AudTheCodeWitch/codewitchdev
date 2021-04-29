---
layout: post
title:      "OurCAL: My Javascript Project"
date:       2019-11-10 20:56:31 -0500
permalink:  ourcal_my_javascript_project
image: /images/heroes/ourcal_js.jpg
image_hero: /images/heroes/ourcal_js.jpg
rainbow_hero: true
---


Hello, friends! I can’t believe it’s time for yet another project review. This bootcamp is flying by, and I am loving every second of the journey! I’m so pleased to have found a career path to pursue that is equally challenging and engaging.


## Choosing a Project

In keeping with my initial goal to have each project reflect my passions, I chose to do my Javascript project on something near and dear to my heart: crochet. My grandmothers taught me to crochet as a little girl, and I’ve developed my craft ever since. Through the years, I have relied on this hobby to soothe my stresses and occupy my fidgety hands. 

One of the most surprising and lovely things about crochet is its amazing online community. From Pinterest and Ravelry, to Facebook groups and a whole host of wonderful blogs, there are a myriad of free resources for my fellow crochet enthusiasts. Of these, Crochet-Alongs, or CALs, for short, are perhaps the most fun. 

In a CAL, crocheters from around the world work on the same project at once, celebrating one another’s differences and creativity as well as teaching and supporting new members of the hobby. I have participated in the [MooglyCAL](https://www.mooglyblog.com/cal-2019-1/) several times, and it inspired me to create my own. 

Similar to the MooglyCAL’s use of unique artists for each segment of their pattern, I wanted a CAL designed for and by the participants. With OurCAL, users design a block, which will typically work up to about a 12” square, and share it with the entire community. Crocheters can then follow the basic corner-to-corner stitch pattern to make whichever blocks they choose! I’m excited to see this app deployed and used by my crochet pals.


## Building OurCAL

Being a Javascript project, the majority of my work this week dealt with the front end of my application — a major shift in focus from previous projects. While writing the HTML and CSS brought back memories of my Neopets coding days (my account may or may not still be active… don’t judge me), this was my first foray into the wonderful world of dom manipulation. I simultaneously loved and cursed Javascript in equal parts as I tweaked my code to make the app behave just the way I envisioned, and I feel as if I learned more from this one project than I did from all the Javascript lessons leading up to it. I’m so thrilled to have pulled it off!

<center><a href="http://www.neopets.com/terms.phtml"><img src="http://images.neopets.com/community/stuff/ac_commentator_anim.gif"  ></a></center>



## Challenges and Breakthroughs

Leave it to me to dream up an app that is far more complicated than the project requirements. I guess I didn’t learn my lesson the last time. While the main focus of this project was to create a single-page application that uses object-oriented Javascript, that was the “easy” part. Building the relationships and fetching information from the back end came together rather quickly. The majority of my struggles this week centered on creating the crochet pattern grids themselves. 


### Creating a Blank Grid

Because I wanted users to be able to select colors and dynamically design their blocks, my first and greatest challenge was to develop what amounts to a pixel art editor. I initially attempted to use HTML5’s `<canvas>` element, but I quickly realized I was in over my head. While I did find a tutorial that would help walk me through the setup, I wanted to pursue a method I could better understand (and thus, explain). Instead, I built the block template by writing a Javascript function that created a series of nested `<div>` elements. I then used CSS styling to keep my grid square.

```javascript

const createBlankBlock = function () {

    let noRows;

    for (noRows = 1; noRows < 26; noRows++) {

        const row = document.createElement('div');

        row.className = 'row';

        row.id = `row-${noRows}`;

        let noCols;

        for (noCols = 1; noCols < 26; noCols++) {

            const pixel = document.createElement('div');

            pixel.className = 'pixel bg';

            pixel.id = `pixel-${noCols}`;

            pixel.style.backgroundColor = 'rgb(255, 255, 255)';

            pixel.addEventListener("click", function() {

                setPixelColor(pixel)

            });

            row.appendChild(pixel);

        }

        blockTemplate.appendChild(row)

    }

};

```

For the color pickers, I imported jscolor, a Javascript library specifically designed for this purpose. I also wrote a function called `setColorPixel()` that fires whenever the user clicks on a box in the grid. When the blocks are initially posted to the database, I used three separate Javascript classes, `User`, `Block`, and `Pixel` to format the data. The block constructor calls on a function within the class which, in turn, creates all 625 pixels.

```javascript

class Block {

    constructor(name, pixels) {

        this.name = name;

        this.pixels_attributes = this.createPixels(pixels);

    }

    createPixels(pixels) {

        let pixelArray = [];

        for(let p of pixels) {

            let coordinates = p.id.split('-')[1];

            let x = coordinates.split(',')[0];

            let y = coordinates.split(',')[1];

            let color = p.style.backgroundColor;

            let color_variable = p.classList[1];

            p = new Pixel(x, y, color, color_variable);

            pixelArray.push(p);

        }

        return pixelArray

    };

}

```


### Rendering Submitted Grids

After a mini dance party to celebrate the successful creation of my block generator and my app’s ability to persist a block to the database, I moved on to the next challenge: rendering blocks fetched from the database. At this point, I had a Pixels table in my database that holds 625 data points for each submitted block. How on earth was I supposed to iterate through those and put them back together to form a picture? I was stumped, but after some good ol’ rubber ducky-ing with my husband (tech writer husbands are the best), I realized I _already have a function to build my blocks_. I just needed to tweak it and figure out how to color them!

I returned to my `createBlankBlock()` function. To make it work in multiple parts of my app, I changed it to take in a `location` argument. I also added some conditional logic so it would only add the default class and event listeners to the block template at the top of the page, leaving the rendered blocks unclickable.

```javascript

const createBlankBlock = function (location) {

    let noRows;

    for (noRows = 1; noRows < 26; noRows++) {

        const row = document.createElement('div');

        row.className = 'row';

        row.id = `row-${noRows}`;

        let noCols;

        for (noCols = 1; noCols < 26; noCols++) {

            const pixel = document.createElement('div');

            if (location.id === 'Template') {

                pixel.className = 'pixel bg';

                pixel.addEventListener("click", function() {

                    setPixelColor(pixel)

                });

            } else {

                pixel.className = 'pixel'

            }

            pixel.id = `${location.id}-${noCols},${26-noRows}`;

            pixel.style.backgroundColor = 'rgb(255, 255, 255)';

            row.appendChild(pixel);

        }

        location.appendChild(row)

    }

};

```

I then wrote a `colorPixels()` function that accepted two arguments, the new `blank` block, and the array of `pixels`. This function loops through the array and changes the background color of the pixels accordingly.

```javascript

const colorPixels = function(blank, pixels) {

    for (let p of pixels) {

        let box = document.getElementById(`${blank.id}-${p.x},${p.y}`);

        box.style.backgroundColor = p.color;

        box.className = `pixel ${p.color_variable}`;

    }

};

```

With these functions in place, fetching the blocks from the database works like a charm!

 


## Ideas for Improvement

<img src="https://i.imgur.com/nCQN01R.jpg?2" alt='My 2017 MooglyCAL blanket' style='float: right' >

Though I am personally blown away by my progress with this app, I do have a few more tweaks I would like to make before deployment. First, I want to add OAuth or some sort of user authentication. As it stands, a user can delete any block, not just his or her own. I also want to add a function that allows the user to see all the blocks rendered in his or her chosen color scheme. If I wanted to make _another_ Ravenclaw-themed blanket,

I could set my colors and have a good idea of how each block would work up in real life. Finally, I would love to build a feature that allows a user to select a number of blocks and arrange them in a blanket. I feel that all of these features are within my grasp; I just need the time to implement them.


## Check It Out

If you’d like to see my app in action, watch the video here:

<center><iframe width="560" height="315" src="https://www.youtube.com/embed/Q4ZJAEO2FJM" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center>

If you’d like to take a look at my code and suggest ways I could improve it (please do!), [check out the repo](https://github.com/AudTheCodeWitch/OurCAL).

