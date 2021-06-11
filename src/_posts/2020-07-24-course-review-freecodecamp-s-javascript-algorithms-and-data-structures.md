---
layout: post
date: 2020-07-24 16:00:00 -0600
title: 'Course Review: FreeCodeCamp''s JavaScript Algorithms and Data Structures'
permalink: course_review_freecodecamps_javascript_algorithms_and_data_structures'
image: /images/heroes/js_algorithms_and_data_structures.jpg
image_hero: /images/heroes/js_algorithms_and_data_structures.jpg
rainbow_hero: true
---
Last week, I completed freeCodeCamp's JavaScript Algorithms and Data Structures course.

![Audrea's JS Algorithms and Data Structures Certificate](/images/fcc-js-algorithms-cert.jpg)

## The Curriculum

Let's break this course down. It is divided into 9 modules, plus a section of 5 projects at the end. Like the Responsive Web Design course ([read my review](https://www.codewitch.dev/course_review_freecodecamps_responsive_web_design "Course Review: FCC's Responsive Web Design")), each lesson has a quick readme with a coding exercise. To advance to the next lesson, your code must pass a set of predefined tests.

### Module 1: Basic JavaScript

Don't let the 110 lessons intimidate you. This section starts with the very basics, such as how to add comments to your code, and builds from there. Being already familiar with the majority of the concepts in this module, the lessons progressed quite quickly. If you are already familiar with JavaScript, this section may not be necessary; however, I found it to be a helpful review, particularly when looking at iteration.

### Module 2: ES6

This 31-lesson module explores ES6, the "most recent standardized version" of JavaScript, which came out in 2015. This section breaks down arrow functions, classes, modules, and more.

I enjoyed practicing object destructuring, like in the example below:

```JavaScript
// Create a module object with 'name' and 'lessons' keys.
const module = { name: 'ES6', lessons: 31 };
    
// Use object destructuring to create variables using the object keys.
// The variable equals the key's value.
const { name, lessons } = module;
  // This is the same as:
  // const name = module.name;
  // const lessons = module.lessons
    
console.log(name);
  // 'ES6'
    
console.log(lessons);
  // 31
```

This section also explained how to import and export your code for reuse. I appreciated the four lessons covering JavaScript Promises, as well.

### Module 3: Regular Expressions

I was a bit terrified to begin this 33-lesson module. Regex has always mystified me, and I thought this section would be no exception.

Perhaps not surprisingly, FreeCodeCamp did a great job explaining how to use `.match()` and `.test()`, as well as all sorts of Regex, to manipulate your JavaScript code.

While I wouldn't say Regex is _easy_ for me, this course, coupled with [Regex101](https://regex101.com/ "Regex 101"), certainly made it _easier_. I now recognize when and how to use Regex, and I no longer balk at doing so.

### Module 4: Debugging

For me, this was the least helpful module in the course. The 12-lesson section on debugging did not do much more than explain how to use `console.log()` to check for common code errors.

### Module 5: Basic Data Structures

For me, this 20-lesson module was a great review of how to manipulate JavaScript arrays and objects. While I've written several blog posts on array manipulation in the past few months, I have not spent as much time studying JavaScript objects. This section refreshed my memory on how to add, remove, and update object keys and values, as well as how to iterate through an object's keys with a `for...in` loop.

### Module 6: Basic Algorithm Scripting

This 16-lesson section is the first of two practice problem sets. These code challenges require you to apply the knowledge from the previous sections.  Challenges like "[Convert Celsius to Fahrenheit](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-algorithm-scripting/convert-celsius-to-fahrenheit)" and "[Factorialize a Number](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-algorithm-scripting/factorialize-a-number)" were great JavaScript exercises that required a bit of math logic to solve, while others were more focused on pure code concepts, like array and string manipulations.

### Module 7: Object-Oriented Programming

We spent a great deal of time learning object-oriented programming at Flatiron, so this was another review section for me. These 26 lessons explore how to structure, alter, and implement JavaScript classes. I found the lessons on constructors and prototypes to be especially helpful.

### Module 8: Functional Programming

Like object-oriented programming, functional programming is a popular approach to writing code.  This 24-lesson section focuses on writing functions to solve coding problems while resisting the urge to transform the given data inputs. This section also reviews common higher-order functions, like `.map()`, `.reduce()`, and `.filter()`.

### Module 9: Intermediate Algorithm Scripting

This is the second set of practice challenges. There are 21 lessons, each more complicated than the last. Some of my personal favorites include "[Spinal Tap Case](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/intermediate-algorithm-scripting/spinal-tap-case)," "[Pig Latin](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/intermediate-algorithm-scripting/pig-latin)," and "[Sum All Odd Fibonacci Numbers](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/intermediate-algorithm-scripting/sum-all-odd-fibonacci-numbers)."

<center>
<img src='https://media.giphy.com/media/PJoFStRf6SEEw/source.gif' alt="Spinal Tap: It's such a fine line between stupid and clever.">
</center>

I found this section to have exercises similar to the ones I have been assigned by companies during my job search, so it was highly valuable practice for me.

## The Projects

To complete this course, learners must complete 5 difficult coding challenges. These projects test your JavaScript knowledge as well as your logic skills. Deciphering the logic required for "[Roman Numeral Converter](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/javascript-algorithms-and-data-structures-projects/roman-numeral-converter)" and "[Cash Register](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/javascript-algorithms-and-data-structures-projects/cash-register)" just about did me in, but it was so satisfying when all the tests finally passed.

<center>
<img src='https://media.giphy.com/media/89x4osEodHEoo/source.gif' alt='Kip saying, "Yes".'>
</center>

_AFTER_ you complete a final project or a lesson in one of the algorithm scripting sections, I highly recommend you visit the **Get a Hint** link in the **Get Help** dropdown. This link often provides a detailed explanation of the logic required, but my favorite part are the possible solutions listed at the bottom. We all know that, with code, there's always more than one way to skin a cat, and I found comparing my solution with the provided ones to be extremely valuable. 

## Final Thoughts

Overall, freeCodeCamp built an excellent course. This one would be more difficult, though not impossible, for an absolute beginner, but I believe it is perfect for a novice. 

My only complaint is this course does not explore the DOM or how JavaScript can be used in tandem with HTML and CSS. A separate course should be added to the freeCodeCamp platform, or this topic should be covered in either this course or the Responsive Web Design Certification.  

Once again, if you have ANY interest in code or web design, I highly recommend starting with [freeCodeCamp](https://www.freecodecamp.org/learn/).
