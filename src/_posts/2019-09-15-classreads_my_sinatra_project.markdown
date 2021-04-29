---
layout: post
title:      "ClassReads: My Sinatra Project"
date:       2019-09-15 17:40:53 -0400
permalink:  classreads_my_sinatra_project
image: /images/heroes/class_reads.jpg
image_hero: /images/heroes/class_reads.jpg
rainbow_hero: true
---


I’ve done it! I’ve designed and built a complete MVC app from start to finish! There were many points along this journey where I thought I may not succeed, but here I am, on the other side. It feels fantastic to know how much I've learned in the past few weeks!

## Choosing a Project
Prior to embarking on this coding adventure, I was a second-grade teacher. I had hundreds of books in my classroom library, but I had no way to track what I had in my inventory, much less know what kinds of books my students were interested in. I remember attempting to use GoodReads to track my books, but it ultimately wasn’t worth the effort. While I was teaching, I never found a solution that really worked for me.

I thought of this problem when brainstorming for this project. While at dinner with some teacher friends, we talked about what a dream classroom library app would do for us: it could track our books, students could leave and read reviews, teachers would have access to data (we’re all about data) they could use to drive instruction and purchase future books for their library. I told my friends I would try to create something magical for them; they have already asked to be beta testers!

## Building My App - MVC Structure
This app has three basic parts: the models, views, and controllers. The models handle the physical data of an application. The views are what the user actually sees, and the controllers act as a go-between for the two of them. Let’s delve into each portion a bit.

### Models

As you can see below, the models tangle together in some confusing ways. A teacher has many books and students, but does not have any reviews. Students belong to a teacher, and they have many reviews. Through the reviews, students also have many books. The reverse is true for books. The reviews table acts as a joining table, even though it also has its own unique attributes.

![Imgur](https://i.imgur.com/d4t40Zn.jpg)

### Views
I had a lot of fun designing the various view pages. In total, this app has 16 different view pages, plus the layout page that creates a cohesive theme throughout the app. Customizing each page through HTML and CSS brought me back to my Neopets days (yeah, I’m getting old), and I had a blast remembering how to tweak a page to look just right. One thing I would like to revise in the future would be the different forms throughout the site. They are functional, but they just aren’t pretty enough. I would also like to add more images to spruce things up a bit.

### Controllers
The controllers portion of my app was by far the most complicated for me. In addition to the `ApplicationController`, I also have a `BooksController`, `StudentsController`, and `TeachersController`. Because the reviews are really just a joiner between books and students, I chose not to create a separate controller for them. Their CRUD (Create, Read, Update/edit, Destroy/delete) actions occur within the `BooksController`.

My `ApplicationController` handles user registration, logging in, and logging out. It also contains a few helper methods used within the application to verify a specific user’s permissions. The `StudentsController` and `TeachersController` are very similar to one another. They both have CRUD routes.

The `BooksController` is the most complicated controller in my application. It has CRUD routes for books. When a book is deleted, it must also delete any associated reviews from both the reviews table and the student’s reviews array. In this way, students only have reviews for books that currently exist in the database. In addition to the CRUD routes for books, the `BooksController` also contains CRUD routes for individual reviews. 

<center><iframe src="https://giphy.com/embed/l1AsL5D0h4RbOh5yU" width="480" height="360" frameBorder="0" class="giphy-embed" allowFullScreen></iframe></center>


## Challenges and Breakthroughs
Overall, this was a challenging project. I ran into many issues throughout the week, but I am proud of my end result. One of the major challenges I encountered was deciding how to structure and seed my database. It took a lot of planning to visualize just how each table would connect to the others. Once I got that built, I still needed to populate my database so I had something to work with. I used the [Faker](https://github.com/faker-ruby/faker) gem to do this, which unintentionally led to the discovery of several bugs I doubt I would have found on my own. In my app’s original design, the URL path for an individual book was something like `/books/title`. I wanted the title in the URL for the sake of the student users. I thought it would be an easy way to quickly go to a book page. As it turns out, different teachers own different copies of the same book. When a student left a review, sometimes that review saved to a different teacher’s book. To solve this problem, I added the book_id into the URL, so now it is `/books/book_id/title`. The title in the URL is no longer necessary, but I chose to leave it for now.

Because I chose to have two different user types, my app required a few extra checks when loading a page. Students could see and do some things, while teachers could see and do other things on the same page. For example, students can only edit their own reviews, but teachers can edit and delete any review. This required a few careful if statements, like the following:

```ruby
<% @book.reviews.each do |r| %>
    <li><h4><%= r.student.name %> gives this book <%= r.rating %> stars!</h4>
      <p><%= r.review %></p>
      <% if current_user.username == r.student.username || session[:role] == 'teacher' %>
        <ul class="edit">
          <li>
            <a href="/books/<%= @book.id %>/<%= @book.slug %>/reviews/<%=r.id %>/edit">
                <button type="button">Edit Review</button>
            </a>
          </li>
          <li><form action="/books/<%= @book.id %>/<%= @book.slug %>/reviews/<%= r.id %>" method="post">
            <input type="hidden" name="_method" value="delete">
            <button type="submit">Delete Review</button>
          </form></li>
        </ul><br><br>
      <% end %>
    </li>
```


This project was as much a lesson in debugging as it was in building a MVC app. Just when I thought my app was running smoothly, I would discover a new issue. Some were simple styling fixes, like making sure all the buttons looked the same and that forms had a standard format. Others, like the book title one described above, required much more brainpower to solve. I found that when I deleted a book or student from the database, it did not always delete the associated reviews. To solve this, I had to add a few lines of code to my delete paths:

```ruby
delete '/books/:id/:slug' do
    @book = Book.find_by_id(params[:id])
    @book.reviews.each {|r| r.destroy}
    @book.save
    @book.destroy
    redirect '/books'
end
```

The third and fourth lines above clear the reviews from a book before the book is deleted, avoiding any future “no-method” errors.

## Ideas for Improvement
Once again, this “finished” project is far from complete. In the future, I would like to add physical star images to the rating system. I would also like to flesh out the student profile section, giving students the opportunity to write an about-me and possibly upload or select an avatar. Allowing students to comment on other reviews could also be a way to increase student engagement on the site.

On the teacher side of things, I would like to create some dashboard-type features, which would allow teachers to better collect and track student data. Specific information about what a student reads and how they respond to it is invaluable as a teacher, especially in the Response to Intervention process. To create more opportunities for data collection, it would be a nice feature for teachers to be able to create quizzes or specific assignments for each book.

## Check It Out
If you’d like to see my application in action, watch the video here:
<center><iframe width="560" height="315" src="https://www.youtube.com/embed/ghpOWOONnn8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center>

If you’d like to take a look at my code and suggest ways I could improve it (please do!), [check out the repo](https://github.com/AudTheCodeWitch/ClassReads).
