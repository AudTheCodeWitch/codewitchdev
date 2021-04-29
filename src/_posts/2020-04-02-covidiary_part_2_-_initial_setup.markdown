---
layout: post
title:      "COVIDiary Part 2 - Initial Setup"
date:       2020-04-02 17:49:44 -0400
permalink:  covidiary_part_2_-_initial_setup
image: /images/heroes/covidiary.jpg
image_hero: /images/heroes/covidiary.jpg
rainbow_hero: true
---


Welcome to Week 2 of the COVIDiary project! If you are new, start at the beginning [here.](https://www.codewitch.dev/covidiary_-_a_rails_react_project)

In an effort to thoroughly document the COVIDiary build process, we are starting at the very beginning this week, laying the groundwork for our project. I am sharing the order in which I completed these tasks, though I realize there are multiple other approaches you could take. Do what works for you. 

At the end of today, we will have:

*   Two separate GitHub repositories
*   GitHub projects to track our work
*   Our basic file structure

## Create Your GitHub Repositories

One of the first decisions we need to make is whether COVIDiary will be built with a mono- or multi- repo pattern. There are pros and cons to both sides, and [this article](https://medium.com/@johnclarke_82232/mono-or-multi-repo-6c3674142dfc) does a great job of explaining them. 

For this project, we will use a multi-repo pattern, housing the frontend and backend in separate GitHub repositories.

1. After logging into your GitHub account, click the plus sign dropdown in the upper-right-hand corner. Then, click “New repository.” 
  <center>
  <img alt="New Repo Dropdown" src="https://i.imgur.com/H5TLCUM.png">
  </center>

2. For your first repo, name it “COVIDiary-client,” add a quick description, check the README box, and pick a license. I usually go with the MIT license, but there are several to choose from. Pick the one you like most. Click the green “Create repository” button.
  <center>
  <img alt="New Repo Form" src='https://i.imgur.com/Le4zhHv.png'>
  </center>

3. Repeat steps 1 and 2, this time naming your repository “COVIDiary-api.”


## Track Your Progress with GitHub Projects (Optional Step)

[GitHub Projects](https://help.github.com/en/github/managing-your-work-on-github/about-project-boards) is a great tool for keeping track of your app’s development. With the ability to create issues and assign them to specific individuals, Projects are even more helpful if you are working on a team. It removes the guesswork about what needs to be done and who needs to do it. 

Just to practice with the Projects workflow, we are going to build one for each of our repos.

1. In your repository, click the “Projects” tab. Then, click the green “Create a project” button.
  <center>
  <img alt="Projects Page" src="https://i.imgur.com/rlkzC59.png">
  </center>

2. Give your project a name and description, and then select a project template. When you’re done, click the green “Create project” button.
  <center>
  <img alt="Project Form" src="https://i.imgur.com/zkhvZkz.png">
  </center>

3. Your project comes populated with cards that explain more about how Projects works. Give them a read, and then archive them.
4. Build your “To do” list. In the “To do” column, click the plus sign, enter your task, and click the green “Add” button.
5. From this point, you can leave the tasks as-is, or you can convert them to issues. I like to use issues so I can assign them to myself and also have a commit record for my ideas. To do this, click the three dots in the right-hand corner of the card and select click “Convert to issue.” Check that the information is correct, and click the green “Convert to issue” button.
6. When you’re working on an issue, move it to “In Progress.” It will automatically move to “Done” when you close the issue. 
  <center>
  <img alt="My API Project Board" src="https://i.imgur.com/652f0CS.png">
  </center>

## Build the Basic File Structure

We’re going to step away from GitHub for a moment. We need to create a home for your local copy of your project. We are going to keep both the frontend and backend projects in a shared parent folder. Complete the following steps in your terminal:

1. `cd` into whatever folder you use to store your dev projects.
2. Make the parent folder with `mkdir COVIDiary`.
3. `cd` into the new folder with `cd ./COVIDiary`.
4. Create the API folder with `mkdir CD-api`.
5. Create the client folder with `mkdir CD-client`.

  <center>
  <img alt="Making our Folders" src="https://i.imgur.com/FnjUsfN.png">
  </center>

## Clone Your Repos

Now, we’ll clone our GitHub repositories into their new homes on our local environment. For this step, we’ll be jumping back and forth between our terminal and GitHub. You’ll complete this process twice, once for each repo.

1. In your browser, navigate to the repo you wish to clone. Click the green “Clone or download” button, and copy the link it provides.
  <center>
  <img alt="Clone Repo Dropdown" src="https://i.imgur.com/wLb8spr.png">
  </center>

2. Back in your terminal, `cd` into the appropriate project folder. For this example, I’m moving into the API folder. 
3. Enter `git clone`, pasting in the link you just copied. 
  <center>
  <img alt="Clone Repo Command" src="https://i.imgur.com/bzujRvJ.png">
  </center>

## Coming Up

We now have everything we need to hit the ground running. Next week, we’ll focus on building out the backend and structuring the PostgreSQL database. In the meantime, keep learning, wash your hands, and stay home! I’m sending you love and virtual (germ-free) hugs.
  <center>
  <img src="https://media.giphy.com/media/GHwokG1NqNmms/source.gif" alt="Virtual Hugs">
  </center>
