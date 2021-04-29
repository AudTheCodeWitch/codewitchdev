---
layout: post
title:      "OurCAL: My React/Redux Project"
date:       2019-12-22 22:40:26 +0000
permalink:  ourcal_my_react_redux_project
image: /images/heroes/ourcal_react.jpg
image_hero: /images/heroes/ourcal_react.jpg
rainbow_hero: true
---

<center>
  <img src='https://media.giphy.com/media/39ChmjbAML62wn3vW9/giphy.gif' alt='This Is It'>
</center>

Holy crackers, I did it. I completed my final project for Flatiron School! This whole experience has been such a boost to my confidence, and I am thrilled to enter the next stage of my journey. But first, let’s talk about OurCal v0.2.0, my final project.


## Choosing a Project

Of all the projects I’ve made while attending Flatiron, OurCal is the one I’m most excited about. It has the most potential to be something I actually deploy and share with the world. My first version, which I discuss [here](https://audthecodewitch.github.io/ourcal_my_javascript_project), was written with basic JavaScript and had limited functionality. It seemed like converting the frontend to React seemed like the perfect choice for this final project.


## Building OurCAL

The backend of my project essentially stayed the same from v0.1.0, but the frontend required a nearly total rewrite. The only thing that remained mostly intact was CSS. Converting my vanilla JavaScript to React with Redux forced me to understand exactly what each component did as well as how it tied into the app as a whole. If you are trying to understand React, I strongly suggest taking an app you are already familiar with and converting it to gain a deeper understanding.


## Challenges and Breakthroughs

Leave it to me to dream up an app that is far more complicated than the project requirements. I guess I didn’t learn my lesson the last time. While the main focus of this project was to create a single-page application that uses object-oriented Javascript, that was the “easy” part. Building the relationships and fetching information from the back end came together rather quickly. The majority of my struggles this week centered on creating the crochet pattern grids themselves. 


### **Properly Documenting the Conversion**

When I decided to upgrade my previous project, I knew I needed to do some research on basic versioning practices. It seemed counterintuitive to me to create an entirely new repo for what is essentially the same app. However, I did not want to lose the record of my previous version, as it is part of my professional portfolio. After reading up on [Semantic Versioning](https://semver.org) and the Release function in GitHub, I decided to create an initial, [v0.1.0 release](https://github.com/AudTheCodeWitch/OurCAL/releases/tag/v0.1.0) for my JavaScript project, which stores that version at its own URL.

After setting my initial release, I read [this awesome guide](https://nvie.com/posts/a-successful-git-branching-model/) about git branching. In it, the author recommends keeping two main branches in your repo: `master` and `develop`. Your `master` branch should always be your most recent, stable release. Any new features and updates live in the `develop` branch until you are ready to release them. When you are ready for a new release, merge your updated `develop` branch with `master`. I used this strategy on this project, and it alleviated many fears I had about accidentally deleting or overwriting something important.

Now, I have records of both versions of my project, as well as a strategy to update and maintain my app.


### **Gotta Give Props**

Let me level with you: I took the week of Thanksgiving off to spend some much-needed time with my mom in Florida. When I returned to Colorado, I did so with a nasty strain of walking pneumonia. Between the break and the fogginess caused by my medications, I really struggled to pick up React, and Redux was completely over my head. I walked into project week exhausted, confused, and terrified. I hadn’t even completed the Redux labs, and I really didn’t understand it. With the support and encouragement from my husband and friends, however, I just pushed through. Looking at it from the other side, React and Redux aren’t nearly as frightening as I first assumed.

One of the most challenging aspects of React and Redux was, for me, the concept of global and local state. I watched countless videos and read so many tutorials, but it still seemed like gibberish to me. 

<center>
  <img src='https://media.giphy.com/media/l0Iy5HPh4IKOMyXAI/giphy.gif' alt='What Does It Mean?!'>
</center>

Because of this confusion, I first built a static app populated by dummy data. Everything looked right, but nothing worked. From there, I tackled what I perceived to be the easiest bits. 

I focused on rendering the completed blocks. First, I created a `cardsReducer` and planned out a few actions. I figured out how to make the delete button work. After that, I configured my Redux store so I could `fetch` completed blocks from the backend.

```javascript

function cardsReducer(state = { all: [] }, action) {

  switch (action.type) {

    case "FETCH_BLOCKS":

      return { all: action.payload };

    case "CREATE_BLOCK":

      return {

        all: [...state.all, action.block.data]

      };

    case "DELETE_BLOCK":

      let block = state.all.find(b => b.id === action.id);

      let index = state.all.indexOf(block);

      return {

        all: [...state.all.slice(0, index), ...state.all.slice(index + 1)]

      };

    default:

      return state;

  }

}

```

I gradually worked up in complexity until I was left with creating a new block and storing color changes. This is where things got super confusing for me. Which component should be responsible for color changes? Does that go in local state or the store? Ultimately, I realized this information belonged in the store so I could easily create the data I needed to save blocks to the backend. For this, we needed another reducer, `blockTemplateReducer`, and the actions `ADD_PIXEL`, `COLOR_PIXEL`, and `CHANGE_COLOR`. The `ADD_PIXEL` action sends the pixel data to the store, and the others focus on updating that store. `ADD_PIXEL` is dispatched in the `Pixel.js` `componentDidMount()`:

```javascript

let x = this.props.column + 1;

    let y = 25 - this.props.row;

    let pixel = {

      x: x,

      y: y,

      color: this.props.colors.bg,

      color_variable: "bg"

    };

    if (this.props.location === "Template") {

      // add pixel to store

      this.props.addPixel(pixel);

    }

  }

```

I actually ended up using local state in only a few places. The most important component with local state was in my `BlockForm.js`. I used local state to create a controlled form, but the submitted data made its way to the store via the `POST_BLOCK` action.

I’m still working on understanding when to use local versus global state, but the practice of actually using both my app clarified so much for me. Bottom line: if a coding concept confuses the hell out of you, just try to use it. You’ll learn so much more than from watching hours of videos. Trust yourself; you can learn this. 


## Ideas for Improvement

While v0.2.0 is an improvement over my previous project, I still have some work to do before I deploy OurCal v1.0.0. I still need to add user authentication and full CRUD capabilities. I also want the user to be able to sort blocks by the designers. After initial deployment, I would like to allow the user to view all the blocks in his or her chosen color scheme. I intend to update the pattern show pages with generated written crochet patterns and a printer-friendly view. Finally, I want to create blanket templates that users can populate and arrange with different designs.


## Check It Out

If you’d like to see my app in action, watch the video here:

<center><iframe width="560" height="315" src="https://www.youtube.com/embed/RMJ_XQH9LGQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center>

If you’d like to take a look at my code and suggest ways I could improve it (please do!), [check out the repo](https://github.com/AudTheCodeWitch/OurCAL). 


## Final Thoughts

I can’t believe this Bootcamp is at its conclusion. I have learned far more than I ever anticipated, and I made great friends along the way. If you are considering stepping out of your comfort zone and learning something new, be it coding, crochet, or underwater basket-weaving, you have my full support. You deserve to take risks, and trust me, the journey will be entirely worth it.

<center>
  <img src='https://media.giphy.com/media/8UF0EXzsc0Ckg/giphy.gif' alt='Mission Accomplished'>
</center>

