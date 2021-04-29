---
layout: post
title:      "JS .map() and .filter() with the Code Witch"
date:       2020-03-19 18:13:47 -0400
permalink:  js_map_and_filter_with_the_code_witch
image: /images/heroes/map_and_filter.jpg
image_hero: /images/heroes/map_and_filter.jpg
rainbow_hero: true
---


<center>

<img src='https://media.giphy.com/media/oNPfwCas8wM0sItsJz/giphy.gif' alt="Yay Spring!"/>

</center>

It’s the first day of spring! Yay for baby animals, and bumblebees, and flowers, and rain showers and… oh, wait. I’m in Colorado, and it’s been snowing since I woke up this morning.

<center>

<img src='https://media.giphy.com/media/QPlE9bpGPRwHe/giphy.gif' alt="It’s so cold!"/>

</center>

Despite the snow and the fact that social distancing is keeping my husband and I cooped up inside, my brain keeps wandering outdoors. While I was supposed to be planning this blog post, I was instead browsing Burpee’s online catalog and rapidly filling my shopping cart. 

So I can go upstairs and brag about how productive and NOT distracted I was today, I’m making the executive decision to use that shopping cart to learn about JavaScript’s `.map()` and `.filter()` methods. Two birds, one stone, baby!

Let’s start off with our shopping cart, which we’ll display as an array of objects. Each object represents a packet of seeds.

<iframe height="400px" width="100%" src="https://repl.it/@MrsAud/Spring-Setup?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>


## .map()

`.map()` is an array method that executes a callback function on each element of a given array. Like `.slice()`, this method is **nondestructive**, meaning the original array will remain unchanged. It returns a new array, populated by the results of the callback function. 

One helpful use for `.map()` is to retrieve specific information from an array of objects. Let’s start playing with our code. Hit “run” to see the output of our functions.

<iframe height="400px" width="100%" src="https://repl.it/@MrsAud/Spring-map?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>

In the above example, our callback function is written out the long way. ES6 allows us to simplify this using the Arrow Function syntax. Let’s refactor, noticing the results stay the same:

<iframe height="400px" width="100%" src="https://repl.it/@MrsAud/Spring-map-refactored?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>


## .filter()

Like `.map()`, `.filter()` is also a **nondestructive** way to manipulate an array. It, again, returns a new array, leaving the original unchanged. It also takes a callback function as an argument, but this callback must return `true` or `false`. The resulting array from `.filter()` is a list of all the elements from the original array for which the callback returns `true`. Let’s take a look:

<iframe height="400px" width="100%" src="https://repl.it/@MrsAud/Spring-filter?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>

Once again, we can refactor this using ES6 syntax:

<iframe height="400px" width="100%" src="https://repl.it/@MrsAud/Spring-filter-refactored?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>


## Getting Fancy

My favorite thing about these methods is how clean they look. They also lend themselves well to chaining, and they are generally fun to experiment with.

<iframe height="400px" width="100%" src="https://repl.it/@MrsAud/Spring-advanced?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>

For a more detailed look at these methods, including optional arguments and more examples, check out MDN’s separate articles on [.map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) and [.filter()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter). If you really want to understand these methods, try them out yourself! Look for points in your code where you might be able to use `.map()` or `.filter()` in lieu of a complicated looping statement, and _just give it a try_. We’re all learning, after all!
