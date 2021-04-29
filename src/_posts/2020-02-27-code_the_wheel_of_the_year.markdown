---
layout: post
title:      "Code the Wheel of the Year"
date:       2020-02-27 19:12:57 -0500
permalink:  code_the_wheel_of_the_year
image: /images/heroes/wheel_of_the_year.jpg
image_hero: /images/heroes/wheel_of_the_year.jpg
rainbow_hero: true
---


Today, we’re going to explore conditional logic in Ruby using the [Pagan Wheel of the Year](https://en.wikipedia.org/wiki/Wheel_of_the_Year). The Wheel of the Year is a set of eight holidays adopted by many Pagan traditions, and each holiday observes the changing of the seasons. 

This witch likes to party. Just kidding, I’m basically a recluse. 

<center>
<img src='https://media.giphy.com/media/THJhZHh2Eu5ws/source.gif' alt="Willow is a spaz"/>
</center>

However, I do like to know when the next holiday is coming up so I can observe it privately or with a few friends. So today, our goal is to write a method that, given a degree of latitude and date, will return the upcoming Pagan holiday. To accomplish this, we will use `if` statements, the ternary operator, and `case` statements.


### Basic Setup

Before we can get into the conditional logic of our program, we need to do some basic setup. First, we’ll require the `date` gem, which allows our program to use the `Date` class. We’ll also get some input from the user to store their location.

<iframe height="400px" width="100%" src="https://repl.it/@MrsAud/WotYSetup?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>


### Determine the Hemisphere

Because the Wheel of the Year is an observation of the seasons, the holidays differ based on one’s location on the globe. For example, when the Northern hemisphere celebrates the winter solstice (Yule), the Southern hemisphere is celebrating the summer solstice (Litha). 

We’ll use an `if` statement in our `#hemisphere` method. Let’s quickly look at the basic syntax:

```ruby

if condition is met

    execute this code

end

```

We can also add an `else` to our statement:

```ruby

if condition is met

    execute this code

else

    execute this code

end

```

If we need more than two options, the `elsif` comes in handy:

```ruby

if condition is met

    execute this code

elsif this condition is met

    execute this code

else

    execute this code

end

```

Back to our program:

<iframe height="400px" width="100%" src="https://repl.it/@MrsAud/WotYHemispheres?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>


### Write the Holiday Methods

Now, we need to write two methods, `#northern` and `#southern`, which, when given a date, return the upcoming holiday. The logic for these two methods is the same, but the holidays are shifted by 6 months. To keep this brief, we’ll only talk through the `#northern` method.

Before we launch into the code, let’s talk about `case` statements and ternary operators. Both of these are used to simplify `if` statements. 


#### Ternary Operator

The ternary operator is used to write simple, one-line `if` statements. The syntax looks like this:

```ruby

# condition ? return-this-if-true : return-this-if-false

# Here’s a quick example:

3 > 5 ? '3 is greater than 5' : '3 is less than 5'

# Returns ‘3 is less than 5’

```


#### Case Statements

`case` statements are used to simplify really long `if` statements. When your `if` statement has three or more `elsif's`, consider switching to a `case` statement. Let’s look at the syntax:

```ruby

# case condition

# when result-1

#     return this code

# when result-2

#     return this code

# when result-3

#     return this code

# when result-4

#     return this code

# when result-5

#     return this code

# else

#     return this code

# end

# Quick example:

x = 5

case x

when 1

  "x is 1"

when 2

  "x is 2"

when 3

  "x is 3"

when 4

  "x is 4"

when 5

  "x is 5"

else

  "x doesn’t match"

end

# Returns ‘x is 5’

```

Returning to our Wheel of the Year, let’s write those methods:

<iframe height="400px" width="100%" src="https://repl.it/@MrsAud/WotYHolidays?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>


### Find the Next Holiday

We’ve just got one more method to bring it all together. This one is for all the marbles:

<iframe height="400px" width="100%" src="https://repl.it/@MrsAud/WotYFinal?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>


### Success!

We did it! Now we’ll always know what the next Pagan holiday is. Next time someone asks you if you understand conditional logic, just channel Endora:

<center>
<img src='https://media.giphy.com/media/YAEbymEIQ581a/source.gif' alt="Endora laughing"/>
</center>

You are a code witch! Of course you do!
