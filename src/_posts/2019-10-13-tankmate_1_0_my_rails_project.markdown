---
layout: post
title:      "TankMate 1.0: My Rails Project"
date:       2019-10-13 23:21:23 -0400
permalink:  tankmate_1_0_my_rails_project
image: /images/heroes/tank_mate.jpg
image_hero: /images/heroes/tank_mate.jpg
rainbow_hero: true
---


How are we back here again? It feels like I just [wrote one of these](https://audthecodewitch.github.io/classreads_my_sinatra_project) project reviews. I can’t believe I’m now well over halfway through this bootcamp journey.


## Choosing a Project

I have maintained aquariums for nearly 20 years. At one point, I had over 300 gallons of freshwater aquariums to keep up with. Tank maintenance was a huge and complicated chore. Once again, I designed the app I wish I had, one that would schedule tasks, track aquarium stocking numbers, and give me a place to record and monitor test results.


## Building TankMate

This app saw me through several firsts. Installing and using PostgreSQL was an adventure, to say the least. Configuring my IDE to use PostgreSQL instead of SQLite was a day-long event that forced me to flex my Google muscle to overcome random errors. Once I got it up and running, I was off to the races, structuring my database with several `has_many` and `has_many_through` relationships:

<center><img src='https://i.imgur.com/1HGDhy6.jpg' alt='Tankmate Database Relationships'></center>


I also used Devise for the first time. Devise is a powerful tool that let me build my user authentication and setup OmniAuth so users can login with Facebook. I highly recommend using Devise because it simplifies the authentication process, but it does take a little configuring to get it working properly. Rails Girls has a very [helpful guide](https://guides.railsgirls.com/devise) for this.

One aspect of TankMate I am particularly proud of is my use of scope methods in my `Maintenance` class. I wanted users to be able to sort maintenance tasks by different criteria, but to do so, I had to add a ton of logic to my controller. As you know, this goes against the idea of Separation of Concerns. With a little refactoring and the use of scope methods, I cleaned up the controller and preserved the use of my sorting function. Here’s what my controller looks like now:

```ruby

helper_method :params

  def index

    @user = User.find(params[:user_id])

    @maintenances = @user.maintenances

    if !params[:tank].blank?

      @maintenances = Maintenance.by_tank(params[:tank])

    elsif !params[:task].blank?

      @maintenances = Maintenance.by_task(params[:task])

    elsif !params[:due].blank?

      @maintenances = if params[:due] == 'Today'

                        Maintenance.today

                      elsif params[:due] == 'Upcoming'

                        Maintenance.upcoming

                      else

                        Maintenance.overdue

                      end

    elsif !params[:status].blank?

      @maintenances = if params[:status] == 'Complete'

                        Maintenance.by_complete

                      else

                        Maintenance.by_incomplete

                      end

    end

  end

```


Here are the scope methods, stored in the Maintenance class, where they belong:

```ruby

def self.by_tank(tank)

    where(tank: tank)

  end

  def self.by_task(task)

    where(task: task)

  end

  def self.today

    where('due =?', Date.today)

  end

  def self.upcoming

    where('due >?', Date.today)

  end

  def self.overdue

    where('due <?', Date.today)

  end

  def self.by_complete

    where(complete: true)

  end

  def self.by_incomplete

    where(complete: false)

  end

```


## Challenges and Breakthroughs


### Forms, Forms, and More Forms

For some reason, I really struggled with forms on this project. I had particular difficulty wiring up my “Schedule Maintenance” form. This is a nested form that leverages the many-to-many relationship between `Tanks` and `Tasks` using `Maintenance` as a join table. With one form, I wanted users to be able to schedule a maintenance task for multiple tanks at the same time. For example, a user may wish to feed the fish in three tanks, but only test the water in one. Instead of submitting the maintenance four times, however, the user only needs to fill it out once per task. As a result, it took me quite a long time to figure out just how to code the `create` method in my `MaintenancesController`. It is probably one of the most unique parts of my app, so let’s step through it:

```ruby

def create

```

If the user does not select a tank, throw an error:

```ruby

  if maintenance_params[:tank_id].length == 1

    @maintenance = Maintenance.new(maintenance_params)

    @maintenance.task_id = set_task(maintenance_params)

    @maintenance.errors.add(:tank_id, :blank, message: "must be selected.")

    @maintenance.save

    render :new and return

```

For each selected tank, create a new `Maintenance` instance:

```ruby

  else

    maintenance_params[:tank_id].each do |t|

      unless t.blank?

          @maintenance = Maintenance.new(maintenance_params)

          @maintenance.tank_id = t

          @maintenance.task_id = set_task(maintenance_params)

          render :new and return unless @maintenance.save

      end

    end

  end

  redirect_to user_maintenances_path(current_user)

end

```

While the `create` method handles the `Tank` and `Maintenance` instances, the `Task` instances are handled within the form itself:

```ruby

<fieldset>

  <legend>Tasks</legend>

    <%= f.collection_select :task_id, Task.all, :id, :title, {include_blank: 'Create New Task'} %>

    <%= f.fields_for :task, Task.new do |t| %>

      <%= t.text_field :title %>

    <% end %>

</fieldset>

```


### MVP


My Rails project was, more than anything, a lesson in prioritization and, to some extent, humility. I entered project week with grand designs for the most beautiful Rails app _OF ALL TIME_. Then life happened. Setting up PostgreSQL took longer than I expected. I had a 2-day migraine that seriously killed my productivity. I was cranky because we went from 80-degree weather to snow overnight (seriously, [Colorado is dumb](https://gazette.com/news/colorado-springs-first-fall-snow-packs-a-punch-leaves-freezing/article_101135f4-ebbf-11e9-a073-234aa734c815.html)). All these factors played a part in the app I present to you today.

<center><img src='https://media.giphy.com/media/RJVHpGEaZ3GkMoQCPp/giphy.gif' alt='Ron Weasley talking about priorities'></center>

Let’s talk about MVP. My entire life, I’ve thought of this acronym as “Most Valuable Person” (not “Player;” I hate sports). I constantly strive to be the MVP in everything I do. Even when there is no competition, I compete with myself. I expect more from myself than anyone will _ever_ expect of me, and this usually leads to pretty great results, albeit with enormous, unhealthy amounts of stress.

My Rails project, and all the struggles I incurred along the way, forced me to shift my perspective of MVP to “Minimum Viable Product.” When my husband suggested this tactic early in the week (probably when I was just starting to annoy him with my frenzied rants about PostgreSQL), I scoffed at the idea. I don’t do “minimum.” In my mind, that equated to “lazy,” which I’m not.

As the week progressed, however, I gradually altered my thinking. I came to realize I had my priorities all out of whack. I was literally making myself ill worrying about things like CSS styling and complicated forms when they weren’t even mentioned in the project requirements. Why was I torturing myself? It’s not like Flatiron is giving out extra credit, y’all. Besides, by focusing on elements I didn’t need, I was neglecting features that were required, and the deadline was swiftly approaching. If I kept it up, I would straight-up fall like a balrog.

<center><img src='http://giphygifs.s3.amazonaws.com/media/njYrp176NQsHS/giphy.gif' alt='You Shall Not Pass'></center>

So I got my priorities straight. I listed out all the things I _wanted_ to do with my app as well as all the things I _needed_ to do. I sorted my list by importance and complexity, and started checking them off one by one. Once I focused, I found the whole process of building TankMate to go much smoother. I still have many features to implement, but now I have an ordered list from which to move forward.


## Ideas for Improvement

I am, overall, very happy with the core functionality of TankMate. It does what I want it to do. My biggest gripe is that it’s ugly. I have no CSS styling. When I have a bit of time, I would like to revisit this app and launch the beautiful app I envisioned at the outset, complete with a fancy gallery wall where users can show off their beautiful aquariums. Once TankMate looks a bit more professional, I plan on deploying it via Heroku. Stay tuned for version 2.0. I will be sure to post a new video walkthrough and blog!


## Check It Out

If you’d like to see my app in action, watch the video here:

<center>

<iframe width="560" height="315" src="https://www.youtube.com/embed/DTcGiADOdbU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

</center>

If you’d like to take a look at my code and suggest ways I could improve it (please do!), [check out the repo](https://github.com/AudTheCodeWitch/tankmate).
