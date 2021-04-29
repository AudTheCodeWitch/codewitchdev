---
layout: post
title:      "Callback Functions with the Code Witch"
date:       2020-01-23 20:07:38 +0000
permalink:  callback_functions_with_the_code_witch
image: /images/heroes/callbacks.jpg
image_hero: /images/heroes/callbacks.jpg
rainbow_hero: true
---


The code witch, now well-versed in [JavaScript closures](https://audthecodewitch.github.io/closures_with_the_code_witch), turned to a blank page in her spellbook. As she pondered the topic for her next entry, the little code witch recalled her technical interview. 

“Of all the topics we discussed, which one was the most embarrassingly obvious?” she mused. “Which one nearly drove me to cast an Unforgivable Curse on myself when I finally matched the term to the code concept?” 

She thought for a moment longer and, with a grim smile, began to write:


## Callback Functions

Callback functions occur frequently in JavaScript. In fact, their presence can be so common that they are easily overlooked. However, callbacks are a powerful bit of code magic, and they are not to be taken lightly.

Put simply, a callback is a function that is passed as an argument inside another function. The callback is then invoked within that parent function. 


### Magic Using Callbacks

Callback functions are relatively simple to define, but a few quick examples will reveal their true power.

<center>
<img src='https://media.giphy.com/media/zdwPmLvAKFwty/source.gif' alt="Hermoine Granger Brewing a Potion"/>
</center>


#### To Name, or Not to Name?

You can use both named and anonymous functions as callbacks. First, we’ll start with the named function:

<p class="codepen" data-height="500" data-theme-id="dark" data-default-tab="js,result" data-user="audthecodewitch" data-slug-hash="LYEqMGK" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Named Callback Function">

  <span>See the Pen <a href="https://codepen.io/audthecodewitch/pen/LYEqMGK">

  Named Callback Function</a> by Audrea Cook (<a href="https://codepen.io/audthecodewitch">@audthecodewitch</a>)

  on <a href="https://codepen.io">CodePen</a>.</span>

</p>

<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

This time, let’s pass an anonymous function as the callback:

<p class="codepen" data-height="496" data-theme-id="dark" data-default-tab="js,result" data-user="audthecodewitch" data-slug-hash="VwYgqQe" style="height: 496px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Anonymous Callback Functions">

  <span>See the Pen <a href="https://codepen.io/audthecodewitch/pen/VwYgqQe">

  Anonymous Callback Functions</a> by Audrea Cook (<a href="https://codepen.io/audthecodewitch">@audthecodewitch</a>)

  on <a href="https://codepen.io">CodePen</a>.</span>

</p>

<script async src="https://static.codepen.io/assets/embed/ei.js"></script>


#### Sync, or Async?

Callbacks can be used in both synchronous and asynchronous code. In both examples above, the callbacks are synchronous, that is, they are executed immediately. Asynchronous callbacks are useful when one wishes to control when specific code is executed, like in event handlers and fetch requests. Let’s look at an example:

<p class="codepen" data-height="624" data-theme-id="dark" data-default-tab="js,result" data-user="audthecodewitch" data-slug-hash="LYEqMwZ" style="height: 624px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Asynchronous Callbacks">

  <span>See the Pen <a href="https://codepen.io/audthecodewitch/pen/LYEqMwZ">

  Asynchronous Callbacks</a> by Audrea Cook (<a href="https://codepen.io/audthecodewitch">@audthecodewitch</a>)

  on <a href="https://codepen.io">CodePen</a>.</span>

</p>

<script async src="https://static.codepen.io/assets/embed/ei.js"></script>


### Danger!

Callbacks are pretty straightforward, but beware of “Callback Hell,” also known as the “Pyramid of Doom.” Callback functions can also take arguments, including other callback functions. This can lead to deeply nested functions that are inefficient and often difficult to debug. 

<center>
<img src='https://media.giphy.com/media/12nfFCZA0vyrSw/source.gif' alt="Ron Weasley Grimacing"/>
</center>

You can avoid this trap by naming your callback functions instead of using anonymous ones. Another workaround is to use promises, which are beyond the scope of today’s post but are [explained in depth here](https://javascript.info/promise-basics).


### Helpful Resources

I found these articles to be particularly helpful in my research. If you are looking for some more information about callbacks, give them a look:



1. [MDN](https://developer.mozilla.org/en-US/docs/Glossary/Callback_function) - Of course I’m sending you to the docs.
2. [JavaScript is Sexy](https://javascriptissexy.com/understand-javascript-callback-functions-and-use-them/) - I mean, they’re right. And they also have a pretty detailed description of callbacks.
3. [Callback Hell](http://callbackhell.com/) - Here’s a deeper look at the dangers of too many callbacks.

