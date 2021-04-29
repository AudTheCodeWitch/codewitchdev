---
layout: post
title:      "Closures with the Code Witch"
date:       2020-01-17 22:13:56 +0000
permalink:  closures_with_the_code_witch
image: /images/heroes/closures.jpg
image_hero: /images/heroes/closures.jpg
rainbow_hero: true
---


<center>
<img src='https://media.giphy.com/media/OPw0yKa8kVfsJdsXKH/giphy.gif' alt="Fresh Prince Intro"/>
</center>

Once upon a time, a little code witch had her first mock technical interview. Her interviewer was super nice, but he asked her lots of questions using terms she had studied, but couldn’t quite remember or explain. She felt quite stupid and discouraged.

When her interviewer showed the code witch an actual example of said technical terms, she literally facepalmed. Now that she could see the code, the little code witch could clearly explain what was happening. The interviewer congratulated her, and she felt slightly less dense.

The code witch realized she spent so much time reading and learning a broad swath of coding concepts over the past few months, but she rarely stopped to smell the roses. She didn’t dig deep into confusing or interesting concepts because the curriculum just kept moving forward, and she couldn’t afford to lag behind.

Now that the code witch is a Flatiron School graduate, she has time to explore the intricacies and nuances of programming. With a set jaw and an eager heart, she created a list of vocabulary terms and confusing topics. Now, the code witch can explore these concepts, work them into her code, and record her findings in her spellbook… err… blog.

Here is her first entry:

## JavaScript Closures

If you have written any JavaScript, chances are, you’ve used a closure, possibly without even realizing it. But what is a closure? Basically, a closure is a function nested within and returned by another function. 

Consider lexical scoping. A closure’s scope has at least three levels: 
1. Its own, local scope
2. Its parent scope (and any grandparents)
3. The global scope

Because of this, closures are useful for emulating private variables. While the closure has access to its parent’s variables, the parent can’t access the closure’s variables.


### Using Closures

Let’s look at an example, using one of the little code witch’s favorite spells:

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="js,result" data-user="audthecodewitch" data-slug-hash="LYEgjYb" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Song of the Witches">

  <span>See the Pen <a href="https://codepen.io/audthecodewitch/pen/LYEgjYb">

  Song of the Witches</a> by Audrea Cook (<a href="https://codepen.io/audthecodewitch">@audthecodewitch</a>)

  on <a href="https://codepen.io">CodePen</a>.</span>

</p>

<script async src="https://static.codepen.io/assets/embed/ei.js"></script>


### Potential Drawbacks

See? Closures aren’t that scary, though the Macbeth witches sure are. There are a couple of drawbacks to using closures in your code, however. First, closures have the potential to cause memory leaks because they can’t be garbage collected until the entire program is done using them. Closures can also lead to some unexpected results when used within loops. Luckily, MDN has a good explanation of how to avoid this in their docs.


<center>
<img src='https://media.giphy.com/media/TITNEEVy0Q8aXmAAdF/giphy.gif' alt="Mr. Kim's Dismissal"/>
</center>


### Helpful Resources

I am far from an expert on Javascript closures, but I certainly know more after researching and writing about it this week. Here are my favorite resources I discovered along the way:


1. [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures) - My husband is a technical writer, folks. Always look at the docs. Somebody worked hard to answer your questions before you even thought to ask them.
2. [W3Schools](https://www.w3schools.com/js/js_function_closures.asp) - Their JavaScript Closures lesson is short and sweet, with a clear, practical example.
3. [Master the JavaScript Interview: What is a Closure?](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36) - This article is the first of several super informative pieces on common JavaScript interview questions. I recommend reading all of them.

