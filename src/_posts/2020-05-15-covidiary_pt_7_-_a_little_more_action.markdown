---
layout: post
title:      "COVIDiary pt. 7 - A Little More Action"
date:       2020-05-15 20:26:37 +0000
permalink:  covidiary_pt_7_-_a_little_more_action
image: /images/heroes/covidiary.jpg
image_hero: /images/heroes/covidiary.jpg
rainbow_hero: true
---


Welcome to Part 7 of the COVIDiary project! If you’re just joining us or missed a post, here’s what we’ve done so far:



*   [Part 1: Project Introduction](https://www.codewitch.dev/covidiary_-_a_rails_react_project)
*   [Part 2: Initial Setup](https://www.codewitch.dev/covidiary_part_2_-_initial_setup)
*   [Part 3: Building the Database](https://www.codewitch.dev/covidiary_pt_3_-_building_the_database)
*   [Part 4: Frontend Setup](https://www.codewitch.dev/covidiary_pt_4_-_frontend_setup)
*   [Part 4.5: Database Fixes](https://www.codewitch.dev/covidiary_pt_4_5_-_database_fixes)
*   [Part 5: Backend Routing](https://www.codewitch.dev/covidiary_pt_5_-_backend_routing)
*   [Part 6: Formatting Data](https://www.codewitch.dev/covidiary_pt_6_-_formatting_data)

This week, we’re going to continue work on the back end, in `CD-API`. By the end of today, we will have basic CRUD actions for our Users and their Entries.

Today’s post will be a little long. Get yourself a Pepsi and some snacks, and settle in, friends.

<center>
<img alt="Go easy on the Pepsi" src="https://media.giphy.com/media/BTtkhBLbMUD16/source.gif">
</center>


### \#public Class Method

If you’ll recall, we added the `is_public` boolean to our `entries` table. We want users to be able to decide if others can see their posts or not. When we fetch from `api/entries`, we should only see the entries that have been marked as public. Let’s add a class method to our `Entry` class in `models/entry.rb`:

```ruby

  # returns all the entries where is_public equals true

  def self.public

    self.all.select {|entry| entry.is_public? == true}

  end

```


### Controller Modifications

Right now, our controllers are basically empty. Let’s build them out a bit. For the moment, we want CRUD (Create, Read, Update/edit, Destroy/delete) actions for both Users and Entries. We will probably tweak these some once we start manipulating data from the front end, but we’ll have a solid start by the end of today.

Let’s start by building out our `UsersController` in `controllers/api/users_controller.rb`. As you look through the following code snippets, remember to read the comments, which are preceded by the `#` symbol.

```ruby

class Api::UsersController < ApplicationController


  # GET api/users

  # This action lists ALL the users in our database

  def index

    users = User.all

    render json: UserSerializer.new(users)

  end


  # POST api/users

  # This action creates a new user, given the provided parameters

  def create

    user = User.create(user_params)

    if user.save

      render json: UserSerializer.new(user)

    else

      render json: { error: "Error creating user" }

    end

  end


  # GET api/users/:id

  # This action shows a specific user, determined by the :id parameter

  def show

    user = User.find(params[:id])

    render json: UserSerializer.new(user)

  end


  # PATCH api/users/:id/

  # This action allows a user to update his or her data.

  def update

    user = User.find(params[:id])

    if user.update(user_params)

      render json: UserSerializer.new(user)

    else

      render json: { error: "Error updating user" }

    end

  end


  # DELETE api/users/:id

  # This action completely removes a user from the database

  # We may want to update this later to also destroy a user's entries

  def destroy

    user = User.find(params[:id])

    user.destroy

  end


  private


  # Determine which parameters to allow from a form submission

  def user_params

    params.require(:user).permit(

        :id,

        :first_name,

        :last_name,

        :email,

        :birth_date,

        :occupation,

        :is_essential,

        :isolation_start,

        :isolation_end,

        :about

    )

  end

end

```

Are you still with me? 

<center>
  <img alt="Dr. House checking in" src="https://media.giphy.com/media/331KYDEYvSGNW/source.gif">
</center>

Let’s add the CRUD actions for our `EntriesController` in `controllers/api/entries_controller.rb`.

```ruby

class Api::EntriesController < ApplicationController


# before we call a controller action, call the #set_user private method

  before_action :set_user


  # GET api/users/:user_id/entries OR api/entries

  # This action lists ALL the entries in the database OR all the entries for a given user.

  def index

    # if there is a user in the params, only show their entries. 

    # Otherwise, only show the public entries.

    # TODO: edit user entries so they only show private ones if it is the current user

    entries = @user ? @user.entries : Entry.public

    options = {

        include: [:user]

    }

    render json: EntrySerializer.new(entries, options)

  end


  # POST api/users/:user_id/entries

  # This action creates a new entry assigned to a given user

  def create

    entry = @user.entries.build(entry_params)

    if entry.save

      render json: EntrySerializer.new(entry)

    else

      render json: { error: "Error creating entry" }

    end

  end


  # GET api/users/:user_id/entries/:id

  # This action shows a specific entry for a given user

  def show

    entry = Entry.find(params[:id])

    options = {

        include: [:user]

    }

    render json: EntrySerializer.new(entry, options)

  end


  # PATCH api/users/:user_id/entries/:id

  # This action allows a user to update his or her entry.

  def update

    entry = Entry.find(params[:id])

    if entry.update(entry_params)

      render json: EntrySerializer.new(entry)

    else

      render json: { error: "Error updating entry" }

    end

  end


  # DELETE api/users/:user_id/entries/:id

  # This action completely removes an entry from the database

  def destroy

    entry = Entry.find(params[:id])

    entry.destroy

  end


  private


  # This method allows us to find a specific user 

  def set_user

    if params[:user_id]

      @user = User.find(params[:user_id])

    end

  end


  # Determine which parameters to allow from a form submission

  def entry_params

    params.require(:entry).permit(

        :id,

        :user_id,

        :health_rating,

        :is_symptomatic,

        :health_comments,

        :mental_health_rating,

        :mental_health_comments,

        :diary_entry,
				
        :is_public,
				
	:created_at

    )

  end

end

```


## Coming Up

Our back end is ready to deliver information to the Client app. Next week, we’ll test that connection with a few `fetch()` requests to make sure everything is running smoothly.

