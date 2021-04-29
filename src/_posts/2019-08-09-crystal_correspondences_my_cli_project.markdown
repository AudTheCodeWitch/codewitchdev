---
layout: post
title:      "Crystal Correspondences: My CLI Project"
date:       2019-08-09 19:12:20 -0400
permalink:  crystal_correspondences_my_cli_project
image: /images/heroes/crystal_correspondences.jpg
image_hero: /images/heroes/crystal_correspondences.jpg
rainbow_hero: true
---

What a whirlwind this week has been! Throughout this CLI Project Week, I rode an emotional and mental rollercoaster that tested my commitment to my programming journey. Now that I’m safely on the other side, I am excited to share my project with you! Let’s dive right in, shall we?

## Choosing a Project
I want my Flatiron projects to reflect my personality and interests. For this project, I also wanted to create something practical; something I might actually use in the future. I am an avid collector of crystals, and I constantly find myself researching the metaphysical properties (or “correspondences” in witch-speak) of new rocks. Wouldn’t it be great if I had a way to gather and read about a bunch of different crystals? 

## Finding a Website
When I first learned about scraping (a whopping two weeks ago), one of my first questions was, “Isn’t this plagiarism?” As a writer and former English literature major, it seemed strange to blatantly take someone else’s work and wrap it up in your own program. 

I was curious about the ethics and legality of web scraping, so I did some extra research over the weekend. I came across[ this awesome blog post](https://benbernardblog.com/web-scraping-and-crawling-are-perfectly-legal-right/), among several others, that lead me to draw a few conclusions of my own. First, web scraping is a giant grey area. While it isn’t strictly illegal, some people would prefer you left their websites alone. It is always a good idea to check a site’s Terms of Service or Robots.txt file before scraping it. Second, there’s no rule that says you *can’t* or even *shouldn’t* make it very clear that the information you gathered is not your own; it is perfectly acceptable to cite your source. Finally, there are several practices I, as a developer, can implement to ensure I am respectful of other members of this amazing technical community. I particularly like and plan to implement the practices described in [this blog post](https://towardsdatascience.com/ethics-in-web-scraping-b96b18136f01?gi=20beb44c1ee8). 

With these new-found guidelines in mind, I set about my search for the perfect, scrapable website. I ruled a few sites out immediately due to their overwhelming use of JavaScript, which rendered them unscrapable (at least, at my current skill level). Others were weeded out because of their Terms of Service. I chose [Beadage.net](https://beadage.net/) because it was scrapable, had all the information (and more!) that I was looking for, and has a very friendly policy towards people wishing to use their page as a resource. I strongly encourage you to check out their site.

## Building My Gem
Once I selected my website, it was time to actually build my Ruby Gem. This was my first experience building a program from scratch, so I was very intimidated at first. I began by outlining my program through commented-out pseudo-code, much in the same way I would approach an essay. I knew where I was starting and where I wanted to end up. Now I just needed to connect the dots.

In hindsight, I could have connected those dots in a more logical, linear fashion. At the beginning of the week, I bounced all over the place. If I got stuck writing one method or class, I simply added a comment about what I was confused with and moved on to another section of my program. I probably wasted a lot of time doing this, but I think it was ultimately beneficial, as I now better understand how all my classes work together to achieve a common goal. It also showed me that I could, in fact, solve tricky problems if I simply thought about them long enough.

## Challenges and Breakthroughs
One of my biggest struggles with this project was getting all my separate files to communicate with one another. I made the naive mistake of renaming and rearranging a few of my files without making sure to reflect those changes throughout my program. A file might work on its own, but because I didn’t change the path in my list of require_relatives, it did not play well with others. I kept running into this issue throughout the week until I ultimately rearranged the file tree so all my classes were in the same folder. The current organization of my program probably is not ideal, but it did solve my problem.

Another issue I encountered was with scraping the website. While scraping the index page was fairly straightforward, the individual crystal pages were much more confusing for me. Instead of having separate or nested div classes for each section of information, all of the elements I wanted to select were listed in the same class. 

![Imgur](https://i.imgur.com/rn3VWDJ.jpg)


To access the information I wanted required a bit of creativity and a lot of trial and error: 
```ruby
if properties_text.include?('Color:')
        color_array = properties_text.split('Color:')[1].strip.split(', ')
      else
        color_array = ['Multicolored Gemstones']
      end
      color_array.map{|color| Color.find_or_create(color)}.each { |color| CrystalColors.create(crystal, color) }
      if properties_text.include?('Type of:')
        purpose_array = properties_text.split('Color:')[0].split('Uses:')[1].strip.split('Type of:')[0].split(', ')
      else
        purpose_array = properties_text.split('Color:')[0].split('Uses:')[1].strip.split(', ')
      end
```

## Ideas for Improvement
Though I am submitting my CLI Project this evening, I in no way think of my gem as “complete.” I am sure my current code could be improved upon, though I don’t see how just yet. Also, I think it would be cool to add a few additional features down the road. First, I would like to reduce the initial load time by changing when the scraper pulls information about each crystal. I also think it would be a helpful feature if the user could enter additional crystals, colors, and properties based on his or her own personal experiences. A final feature I would like to see in the future is the ability to export the database to a CSV or other type of file. 

## Teamwork Makes the Dream Work
Though I am immensely proud of my progress this week, I would be remiss if I did not mention my fantastic support system. Without my family, the awesome members of my GitIt-Togthr cohort, and my coaches, Morgan and Talia, I would have been completely overwhelmed by this project. Thanks, guys. Y’all are the real MVPs.


## Check It Out
If you’d like to see my Gem in action, watch the video here:
<center><iframe width="560" height="315" src="https://www.youtube.com/embed/ga9A9cXGLdE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center>

If you’d like to take a look at my code and suggest ways I could improve it (please do!), [check out the repo](https://github.com/AudTheCodeWitch/crystal_correspondences).



