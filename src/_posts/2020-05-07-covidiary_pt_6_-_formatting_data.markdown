---
layout: post
title:      "COVIDiary pt. 6 - Formatting Data"
date:       2020-05-07 15:54:52 -0400
permalink:  covidiary_pt_6_-_formatting_data
image: /images/heroes/covidiary.jpg
image_hero: /images/heroes/covidiary.jpg
rainbow_hero: true
---

Welcome to Part 6 of the COVIDiary project! If you’re just joining us or missed a post, here’s what we’ve done so far:


*   [Part 1: Project Introduction](https://www.codewitch.dev/covidiary_-_a_rails_react_project)
*   [Part 2: Initial Setup](https://www.codewitch.dev/covidiary_part_2_-_initial_setup)
*   [Part 3: Building the Database](https://www.codewitch.dev/covidiary_pt_3_-_building_the_database)
*   [Part 4: Frontend Setup](https://www.codewitch.dev/covidiary_pt_4_-_frontend_setup)
*   [Part 4.5: Database Fixes](https://www.codewitch.dev/covidiary_pt_4_5_-_database_fixes)
*   [Part 5: Backend Routing](https://www.codewitch.dev/covidiary_pt_5_-_backend_routing)

This week, we’re working on the back end. By the end of today, we will:


*   Add some important gems
*   Generate serializers to properly format our data

Are you ready? Let’s do this.

<center>
  <img alt="Let’s do this!" src="https://media.giphy.com/media/JykvbWfXtAHSM/giphy.gif">
</center>

Open your `CD-API` repository. 
## 1. Add Gems
We need to add two more gems to our `Gemfile` to help the front and back ends communicate properly.

### Rack CORS Middleware
The first is Rack CORS Middleware, which will let our fetch requests work. Rack CORS is used so frequently in Rails applications that it’s automatically included in your `Gemfile`. To use it, simply uncomment the line in your `Gemfile`.

```ruby
# Use Rack CORS for handling Cross-Origin Resource Sharing (CORS), making cross-origin AJAX possible
gem 'rack-cors'
```

We also need to uncomment the following section in `config/initializers/cors.rb`:

```ruby
Rails.application.config.middleware.insert_before 0, Rack::Cors do
  allow do
    origins 'example.com'

    resource '*',
      headers: :any,
      methods: [:get, :post, :put, :patch, :delete, :options, :head]
  end
end
```

Finally, change `example.com` to `*` for now.

### Fast JSON API
The second gem we need to add is Fast JSON API. This will allow us to generate serializers and properly format our data before sending it to the front end. You can read more about serializers here. In your `Gemfile`, add the following:

```ruby
gem ‘fast_jsonapi’
```

That’s it! Now that we’ve added both gems, let’s install them by running `bundle install` in your terminal. You can also start up your backend server now using `rails s`.

## 2. Generate Serializers
We need a serializer for both our `Entries` and our `Users`. 

<center>
  <img alt="Get that cereal!" src="https://media.giphy.com/media/3o85xKRIokv92FRo52/source.gif">
</center>

With Fast JSON API, these are easy to create with the `rails g serializer` command. Let’s do that now. In your terminal, enter the following:

```
rails g serializer Entry
rails g serializer User
```

You will now have a `serializers` directory in your `app` directory, and it will contain your two new serializer files. They should look something like this:

```ruby
class EntrySerializer
  include FastJsonapi::ObjectSerializer
  attributes 
end
```

Let’s configure these to present the data the way we want. First, we’ll add our relationships. A user has many entries, so in your `UserSerializer` class, add:

```ruby
has_many :entries
```

We’ll set up the opposite side of the relationship in your `EntrySerializer` class:

```ruby
Belongs_to :user
```

Now that we have the relationships under control, we need to specify which data attributes we want to serialize. In your `EntrySerializer` class, change the `attributes` line to look like the following:

```ruby
attributes :id,
             :health_rating,
             :is_symptomatic,
             :health_comments,
             :mental_health_rating,
             :mental_health_comments,
             :diary_entry,
             :is_public,
             :created_at
```

Now do the same with the `UserSerializer` class:

```ruby
attributes :id,
             :first_name,
             :last_name,
             :email,
             :birth_date,
             :occupation,
             :is_essential,
             :isolation_start,
             :isolation_end,
             :about
```
## Coming Up
We now have serializers to properly format our data for future `fetch()` requests!! Next week, we’ll create our controller actions so we can finally connect to the front end!

