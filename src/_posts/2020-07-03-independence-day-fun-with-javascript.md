---
layout: post
date: 2020-07-03 13:43:35 -0600
title: Independence Day Fun With JavaScript
permalink: independence_day_fun_with_javascript
image: /images/heroes/fireworks.jpg
image_hero: /images/heroes/fireworks.jpg
rainbow_hero: true
---
If you live in the USA, Happy Independence Day! I've been busy this week doing family stuff, so I honestly haven't touched the COVIDiary project. We'll hopefully get back into that in the next week or so.

Instead, I thought we'd have a little fun with JavaScript today. We are going to use HTML, CSS, and JavaScript to create the American Flag!

## Starter Code

This tutorial is focusing on JavaScript, so I have provided the HTML and CSS for you. When you finish the tutorial, feel free to play with the CSS properties to see how they work. I added comments to the code so you know what each line does.

Here's the starter code. If you want to code along, I suggest clicking the **Edit on CODEPEN** button and putting that tab in a new window.

<p class="codepen" data-height="500" data-theme-id="dark" data-default-tab="html,result" data-user="audthecodewitch" data-slug-hash="RwrxOxZ" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="US Flag (Starter Template)">
<span>See the Pen <a href="https://codepen.io/audthecodewitch/pen/RwrxOxZ">
US Flag (Starter Template)</a> by Audrea Cook (<a href="https://codepen.io/audthecodewitch">@audthecodewitch</a>)
on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

I provided a blank flag template via HTML and CSS. You are going to add the JavaScript to create the field of stripes and the union (the blue square with stars) using two separate functions. I've separated the functions into the two embedded CodePens below, but you'll add the code for both to your JavaScript tab in your CodePen!

## The `stripes()` Function

This function will create our 13 red and white stripes. Read the comments for each line to see what it's doing.

<p class="codepen" data-height="500" data-theme-id="dark" data-default-tab="js,result" data-user="audthecodewitch" data-slug-hash="jOWYRXR" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="US Flag (Stripes)">
<span>See the Pen <a href="https://codepen.io/audthecodewitch/pen/jOWYRXR">
US Flag (Stripes)</a> by Audrea Cook (<a href="https://codepen.io/audthecodewitch">@audthecodewitch</a>)
on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

## The `stars()` Function

This function will create our blue union with the 9 rows of white stars. The stars are FontAwesome icons.Please note the location of union within our flag container is determined by the CSS `#union` id. 

<p class="codepen" data-height="500" data-theme-id="dark" data-default-tab="js,result" data-user="audthecodewitch" data-slug-hash="bGEaJXz" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="US Flag (Stars)">
<span>See the Pen <a href="https://codepen.io/audthecodewitch/pen/bGEaJXz">
US Flag (Stars)</a> by Audrea Cook (<a href="https://codepen.io/audthecodewitch">@audthecodewitch</a>)
on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

## Bippity-Boppity Boo! (Put it Together)

If you've been coding along, you should have a beautiful US flag! If not, here's what it looks like when the two functions are put together.

<p class="codepen" data-height="500" data-theme-id="dark" data-default-tab="js,result" data-user="audthecodewitch" data-slug-hash="ExPbPQZ" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="US Flag (Complete)">
<span>See the Pen <a href="https://codepen.io/audthecodewitch/pen/ExPbPQZ">
US Flag (Complete)</a> by Audrea Cook (<a href="https://codepen.io/audthecodewitch">@audthecodewitch</a>)
on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

I hope you had as much fun with this as I did! Have a safe and wonderful 4th of July!
