---
layout: post
title:      "COVIDiary pt. 5 - Backend Routing"
date:       2020-05-01 21:07:44 +0000
permalink:  covidiary_pt_5_-_backend_routing
image: /images/heroes/covidiary.jpg
image_hero: /images/heroes/covidiary.jpg
rainbow_hero: true
---


Welcome to Part 5 of the COVIDiary project! If you’re just joining us or missed a post, here’s what we’ve done so far:



*   [Part 1: Project Introduction](https://www.codewitch.dev/covidiary_-_a_rails_react_project)
*   [Part 2: Initial Setup](https://www.codewitch.dev/covidiary_part_2_-_initial_setup)
*   [Part 3: Building the Database](https://www.codewitch.dev/covidiary_pt_3_-_building_the_database)
*   [Part 4: Frontend Setup](https://www.codewitch.dev/covidiary_pt_4_-_frontend_setup)
*   [Part 4.5: Database Fixes](https://www.codewitch.dev/covidiary_pt_4_5_-_database_fixes)

This week’s post **was** super duper long, and it covered lots and lots of code across the front and back end. My inner editor put her foot down, and I have now broken that massive tome into not one, but four smaller posts that focus on specific concepts or tasks.

<center>
  <img src="https://media.giphy.com/media/i5yobxd9zkMBq/source.gif" alt="No more books">
</center>

If you want to skip ahead, you can check out my progress in the [CD-API ](https://github.com/AudTheCodeWitch/COVIDiary-api) and [CD-Client ](https://github.com/AudTheCodeWitch/COVIDiary-client) repositories on GitHub. I’ll continue working on the project as these blog posts release over the coming weeks.

Today, we’re going to work on the back end. By the end of today, we will have all our backend routing configured and ready to go.

<center>
  <img alt="Old-fashioned switch board" src="https://media.giphy.com/media/ilqP03ohzeIJZGnnpe/source.gif">
</center>

Open your `CD-API` repository. 


## Namespace Routes

We’ll start by configuring our routes. We want to add `/api` to our backend routes so we can better keep things straight. 

To keep our files organized, make an `/api` directory in your `/controllers` directory, and place your controllers within it.

<center>
  <img alt="Controller file structure" src="https://i.imgur.com/kHOYJ6m.jpg">
</center>

Note: You probably don’t have the `users_controller.rb` yet. If that’s the case, now is a perfect time to add it. In your terminal, run `rails g controller api/users`.

Now we’ll wrap our resources within an `/api` namespace in our `config/routes.rb` file:

```ruby

rails.application.routes.draw do

  # wrap routes in /api namespace

  namespace :api do

    # create index route for all entries at /api/entries

    resources :entries

    # create routes for users at /api/users

    resources :users

  end

end

```

We only want `/api/entries` so we can see the list of all public entries. We want to nest our CRUD actions for specific entries under specific users. Let’s make some minor changes to accomplish this.

```ruby

rails.application.routes.draw do

  namespace :api do

    # creates index route for all entries at /api/entries

    resources :entries, only: [:index]

    resources :users do

      # create all CRUD routes for a specific user's entries at api/users/:user_id/entries

      resources :entries

    end

  end

end

```

At this point, you can run `rails routes` in your terminal to see all the routes we’ve just created.

<center>
  <img alt="Hell Yeah!" src="https://media.giphy.com/media/fWj2TR9mfYJ56/source.gif">
</center>


## Coming Up

We are one step closer to hooking up our front and back ends. Next week, we’ll format our data so we can send it to our client app. We’re making progress!

