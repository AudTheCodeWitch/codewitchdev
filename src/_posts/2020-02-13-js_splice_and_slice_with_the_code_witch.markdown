---
layout: post
title:      "JS .splice() and .slice() with the Code Witch"
date:       2020-02-13 14:11:59 -0500
permalink:  js_splice_and_slice_with_the_code_witch
image: /images/heroes/splice_and_slice.jpg
image_hero: /images/heroes/splice_and_slice.jpg
rainbow_hero: true
---


<center>
<img src='https://media.giphy.com/media/5xtDarLi6Rr6F8ffdxm/source.gif' alt="Magic Potions"/>
</center>


Tomorrow is Valentine’s Day, so today, we’re talking about love. When it comes to JavaScript data structures, I love arrays. What’s more, I love manipulating them with array methods! In addition to `.pop()`, `.push()`, `.shift()`, and `.unshift()`, there are many other pre-built methods used for changing and rearranging arrays.

Two of these methods, `.splice()` and `.slice()` are powerful tools that sound similar but are very different. To reveal the magic of these methods, let’s take an array of love potions. Feel free to follow along in your console:

```javascript 
let lovePotions = ["No.1", "No.2", "No.3", "No.4", "No.5", "No.6", "No.7", "No.8", "No.9", "No.10"] 
```


## .splice()

The JavaScript array method, `.splice()`, is used for adding and/or removing elements at a given index, similar to _splicing_ two electrical wires. Some things to note about `.splice()`:

*   This method is **destructive**, meaning it will permanently alter the original array.
*   This method **returns** the removed items, not the altered array.
*   This method accepts three types of parameters, the index, the number of elements to be removed, and any number of elements to be added. Only the index parameter is required

Let’s play with our potions. First, we’ll take a look at the format for `.splice()`:

```javascript 
// array.splice(index, numberToDelete, ...addedElements) 
```

We don’t want Love Potion No.3. It has some… unexpected results.

<center>
<img src='https://media.giphy.com/media/P2yDcLYrf4is/source.gif' alt="Donkey took a potion, and now he's a horse."/>
</center>


Let’s get rid of it.

```javascript
lovePotions.splice(2, 1)

// Returns [“No.3”]


console.log(lovePotions)

// Returns  ["No.1", "No.2", "No.4", "No.5", "No.6", "No.7", "No.8", "No.9", "No.10"]
```


Instead of Love Potion No.3, let’s substitute it with a few new concoctions:

```javascript 
// Note the second parameter is 0 because we don’t want to remove any elements.

lovePotions.splice(2, 0, "No.11", "No.12")

// Returns [ ]

// Remember, .splice returns the removed elements. We didn’t remove any, so the return is just an empty array.


console.log(lovePotions)

// Returns ["No.1", "No.2", "No.11", "No.12", "No.4", "No.5", "No.6", "No.7", "No.8", "No.9", "No.10"]
```


Oops! Those potions were WAY more havoc-wreaking than No.3. Let’s get rid of them and put No.3 back where it belongs. Pay attention to the second and third parameters, here. We’re _deleting_ two elements and _adding_ one:

```javascript 
lovePotions.splice(2, 2, “No.3”)

// Returns our removed potions, ["No.11", "No.12"]


console.log(lovePotions)

// Returns ["No.1", "No.2", "No.3", "No.4", "No.5", "No.6", "No.7", "No.8", "No.9", "No.10"]
```


After much testing, we’ve found our best potion. Let’s set it aside for later:

```javascript 
let best = lovePotions.splice(8, 1)


// Can you guess which potion it is? Remember, the index of an array starts at 0.

// ...

// ...

// ...

// ...

// ...

console.log(best)

// Returns [“No.9”]


console.log(lovePotions)

// Returns ["No.1", "No.2", "No.3", "No.4", "No.5", "No.6", "No.7", "No.8", "No.10"]
```


## .slice()

JavaScript’s array method, `.slice()`, is used to select a specific number of elements from an array. Some things to remember about `.slice()`:

*   This method is **nondestructive**, meaning the original array will be left unchanged
*   This method **returns** a new array of the selected items
*   This method accepts up to two parameters, the starting index and the index _after_ the end of the new array.

We know a few potions work. Let’s create a separate list for them:

```javascript 
let workingPotions = lovePotions.slice(3, 8)

// Can you figure out which potions work? Take a guess.

// ...

// ...

// ...

// ...

// ...

console.log(workingPotions)

// Returns ["No.4", "No.5", "No.6", "No.7", "No.8"]


// Remember, our lovePotions array is unharmed. Take a look:

console.log(lovePotions)

// Returns ["No.1", "No.2", "No.3", "No.4", "No.5", "No.6", "No.7", "No.8", "No.10"]
```


If you don’t specify the first parameter, `.slice()` starts at the beginning of the array.

```javascript 
lovePotions.slice(null, 3)

// Returns ["No.1", "No.2", "No.3"]

```


If you don’t specify the second parameter, `.slice()` stops at the end of the array.

```javascript
lovePotions.slice(7)

// Returns ["No.8", "No.10"]
```


If you’re feeling fancy, you can use negative numbers to select elements starting at the end of the array.

```javascript
lovePotions.slice(-4, -2)

// Returns ["No.6", "No.7"]
```

## Bonus

With Valentine’s Day coming up tomorrow, our love potions are in high demand. Let’s use `.splice()` and `.slice()` to arrange the potions from best to worst. We’ve already figured out a few of the rankings. Here’s what we’ll start with:

```javascript
// Create an empty array for our sorted potions

let rankedPotions = []


console.log(bestPotion)

// Returns ["No.9"]


console.log(workingPotions)

// Returns ["No.4", "No.5", "No.6", "No.7", "No.8"]
```


Potions No.1 and No.2 simply don’t work.

```javascript 
let brokenPotions = lovePotions.slice(0, 2)

// Returns ["No.1", "No.2"]
```


Through some unfortunate trials, we discovered that potions No.3 and No.10 are toxic. Let’s use both methods we’ve learned today.

```javascript 
// First, we’ll create a copy of the lovePotions array, starting at potion No.3 and ending at No.10.

let toxicPotions = lovePotions.slice(2)

// Returns ["No.3", "No.4", "No.5", "No.6", "No.7", "No.8", "No.10"]


// Let’s get rid of the nontoxic potions from our new array. Remember the return value of .splice()

toxicPotions.splice(1, 5)

// Returns ["No.4", "No.5", "No.6", "No.7", "No.8"]


console.log(toxicPotions)

// Returns ["No.3", "No.10"]
```


Now that we’ve grouped our potions, let’s use `.splice()` to add them to our `rankedPotions` array. We aren’t removing any elements, so the first two arguments will be 0. The remaining parameters are the variables we’ve created, in the order we want them.

```javascript 
rankedPotions.splice(0, 0, bestPotion, workingPotions, brokenPotions, toxicPotions)

// Returns [ ]


console.log(rankedPotions)

// Can you predict the return value?

// ...

// ...

// ...

// ...

// ...

// Returns [ [“No.9”], ["No.4", "No.5", "No.6", "No.7", "No.8"], ["No.1", "No.2"], ["No.3", "No.10"] ]
```


Whoa! We don’t want the customers to see the potions lumped into separate groups. They might get a bit suspicious. Let’s flatten that out.

```javascript 
rankedPotions = rankedPotions.flat()

// Returns ["No.9", "No.4", "No.5", "No.6", "No.7", "No.8", "No.1", "No.2", "No.3", "No.10"]
```


Beautiful! Now we have all our love potions ready to go! Whether you have a Valentine or not tomorrow, you can celebrate your new-found love for JavaScript’s `.splice()` and `.slice()`!

<center>
<img src='https://media.giphy.com/media/l0HUdL0aZXLBNXy2A/source.gif' alt="You're my type Valentine"/>
</center>

