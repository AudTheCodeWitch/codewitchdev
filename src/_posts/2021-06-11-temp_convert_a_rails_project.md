---
layout: post
date: 2021-06-11 14:30:00 -0600
title: 'Temp Convert: a React Project'
permalink: temp_convert_a_react_project
image: /images/heroes/temp_convert.jpg
image_hero: /images/heroes/temp_convert.jpg
rainbow_hero: true
---

Dusting the ol' blog off to share a fun project I built this week. This was a fun coding
challenge presented to me by a prospective employer (that's right, friends. I'm looking for my next gig), and I couldn't
*not* share it with you, my devoted ~~crickets~~ readers. Allow me to present Temp Convert, a simple React SPA
that takes a temperature in one scale (Fahrenheit or Celsius) and converts it to the opposite scale. 

**Note: the rest of this is copied straight from my project's [README](https://github.com/AudTheCodeWitch/temp-convert). 
It's Friday, y'all!**

### ✨ [Demo](https://affectionate-mcnulty-5e14aa.netlify.app)

### Features
**Temperature Conversion**

This is the core feature of Temp Convert. Users can enter a number in either of the two fields (one for Fahrenheit and
one for Celsius), and the opposite field will automatically update to display the converted temperature. The temperature
conversion feature is comprised of two components, `Calculator` and `TempInput`.

`TempInput` is responsible for displaying an input field for a given temperature scale. It receives the following
props from `Calculator`:
* `temp` -> the temperature value to display
* `scale` -> `c` for Celsius and `f` for Fahrenheit
* `onChange` -> determines which calculation to complete when the input changes

`Calculator.js` is responsible for holding the state as well as all the calculation logic. The component comes with three
additional functions:
* `toCelsius()` -> takes a temperature (in Fahrenheit) and returns the converted temperature in Celsius
* `toFahrenheit()` -> takes a temperature (in Celsius) and returns the converted temperature in Fahrenheit
* `convert()` -> takes a temperature and converter function. If the temperature is `NaN`, it simply returns an empty
  string. Otherwise, it rounds the converted temperature to the first decimal place and returns the result as a string.

The component itself has two event handlers, both of which update the state to the correct temperature scale. These
handlers are passed as the `onChange` prop to `TempInput`.

Within the `render()` function, there are a few variables. `scale` and `temp` are grabbed from the state. `c` and `f`
check the `scale`. If the `scale` from the state is set to the opposite scale, call `convert()` to calculate the appropriate
temperature. Otherwise, simply return the `temp`. The variables, `c` and `f`, are passed to `TempInput` as the `temp`
prop.

**Light/Dark Mode**

Light/Dark Mode is a bonus feature for this project. It changes the color scheme, depending on the user's selection. The
entire functionality is contained in `DarkModeToggle.js`. Color scheme styling is housed in `index.css` and
`tailwind.config.js`.

The color schemes are defined in `index.css`. For each parent class, there are individual variables for the main styling
elements used throughout the application (background, text, and border). These variables are then used in `tailwind.config.js`
to configure the specific Tailwind color classes, like `bg-primary`.
This approach allows the developer to add as many color schemes as they want. As long as the variable names are consistent,
the app will display as expected. Right now, there are only two themes (light and dark), but this lays the groundwork for
future theming opportunities.

The `DarkModeToggle` sets the initial state to light mode by default. This state is toggled by the `handleModeChange()`
event handler when a user clicks the toggle button (displayed as an icon).

Within the `render()` function, there is a simple conditional statement. If the mode (retrieved from the state) is `'light'`,
set the icon image to a moon and apply the `light` CSS class to the `root` element. Otherwise, set the icon to a sun and
apply the `dark` CSS class.

## Technical Decisions

### Application Architecture
Currently, Temp Convert has a relatively simple architecture. Individual component files are housed in `./src/components`,
while image assets (the CodeWitch logo and various icons) are stored in the `./src/assets` directory. All CSS is handled
in `tailwind.config.js`, `index.css`, or within the components themselves. Because this is a MVP, there is no need for a
more complicated structure.

Further iterations of this application may see a slightly more complicated file structure. For example, each component
could live in its own directory, along with any corresponding test or CSS files. As more features evolve, it may also make
sense to include a `./src/containers` directory to keep `App.js` from getting too cluttered. An example of this would be
if the application were to have multiple calculators within the main body of the page.

### UI/UX Design
Temp Convert has a simple job: take a temperature in one scale and convert it to another. I wanted the interface to reflect
this simplicity and be self-explanatory.
* The application follows the normal Header -> Body -> Footer structure we are all used to seeing to facilitate ease of use.
* There is very little text on the screen, but alt text and labels are included for screen readers and accessibility.
* This application is responsive, developed with a mobile-first approach. On mobile, the inputs are stacked vertically,
  and the two-arrow conversion icon points up and down. On tablet screens and larger, the inputs are displayed horizontally,
  with the icon pointing left and right.
* Users can type in either temperature input. The selected input is highlighted with a border in a contrasting color.
* The color schemes, both light and dark, were chosen with accessibility in mind. The application is still highly legible
  at multiple levels of visual color impairment.
* Fonts and icons were chosen to accent the fun, cheerful vibe of the application as well as to correspond with my personal
  brand as the Code Witch.

### Tools and Frameworks
**React via [Create React App](https://reactjs.org/docs/create-a-new-react-app.html#create-react-app)**

A few reasons led to my decision to build this application in React:
* React's reusable component structure allows you to build complicated UIs while keeping the code DRY and organized.
* Because all logic is handled on the client side for this application, there is currently no need for a backend or
  database. However, if I were to add a backend in the future, React integrates well with Ruby on Rails, my backend
  framework of choice.
* Create React App is a simple way to build a single-page application that generates the basic file structure of your application.
  It also preconfigures necessary tools like webpack and Babel, saving the developer time during the initial setup.

**[Tailwind CSS](https://tailwindcss.com/)**

Tailwind CSS is a great CSS framework. I chose to use it for several reasons:
* It is conducive to mobile-first development with preconfigured breakpoints for various devices.
* When built for production, Tailwind purges unused CSS, keeping your files smaller.
* Tailwind has solid documentation, making it easy to learn and use.

**[The Noun Project](https://thenounproject.com/)**

All icons for this application were found on The Noun Project. Their extensive icon collection is free to use with
attribution. Alternatively, you can purchase icons individually or get unlimited access for a reasonable flat fee.

**[Colormind](http://colormind.io/)**

Colormind is a color scheme generator. It is a great starting point for choosing a color scheme because you can preview
how the palette might be applied to an actual website.
