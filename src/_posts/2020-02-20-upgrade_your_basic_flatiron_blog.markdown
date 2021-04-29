---
layout: post
title:      "Upgrade Your Basic Flatiron Blog"
date:       2020-02-20 17:22:35 -0500
permalink:  upgrade_your_basic_flatiron_blog
image: /images/heroes/upgrade_blog.png
image_hero: /images/heroes/upgrade_blog.png
rainbow_hero: true
---


Y’all know by now that I am a Flatiron graduate. As one of their many program requirements, students are expected to keep a technical blog (which you’re reading). They make it super simple by setting one up for you using GitHub Pages (which hosts your blog for FREE). 

Unfortunately, your blog looks identical to those of all your Flatiron classmates.

<center>
<img src='https://media.giphy.com/media/Fff5OHrhY19sY/source.gif' alt="Star Wars Clones"/>
</center>

Where’s the magic in that? Let me walk you through a few _dead simple_ ways to take your blog to the next level.


## Get That Domain

You guys, I did a thing. I finally purchased a custom domain for my blog. Welcome to codewitch.dev! After realizing how quick and easy this was, I’m now kicking myself for not handling it earlier. Here’s how I did it:


1. Purchase a domain name on a site like Namecheap (that’s who I used). Come up with a name that’s relevant and memorable. I like the `.dev` extension because it tells visitors exactly what they are getting with my site.
2. We need to add 5 DNS records to your new domain. On Namecheap, you can do this under the Advanced DNS tab. Copy these records, substituting your GitHub username for the `CNAME`:

    <center>
    <img src='https://i.imgur.com/mysawbK.jpg' alt="DNS Records"/>
    </center>

3. Now, navigate to the `Settings` tab on your blog’s GitHub repository, and scroll down to the `GitHub Pages` section. Enter your new domain in the provided text box and click `Save`. When available (it took about 5 minutes for me), refresh the page and check the `Enforce HTTPS` box. 

    <center>
    <img src='https://i.imgur.com/ZpwtU8f.jpg' alt="Custom Domain Settings on GitHub"/>
    </center>

4. Visit your new domain! Keep in mind, you may have to wait up to 24 hours for all your changes to take effect. Don’t do this right before your next blog post is due.


## Update Your Background Images

Right now, your blog is built using the Jekyll version of Start Bootstrap’s Clean Blog theme. Flatiron took care of a lot of the configuration for you, but their choice in background images is a little too… blue for me. Let’s fix that!



1. Find some images that fit your personality. I recommend Pixabay for free and ready-to-go pictures, but you can always create your own, as well. I used an image editor to resize my galaxy picture so it fits _just right_ (1299 x 448 pixels).
2. In your blog’s repo, add your new pictures to the `/img` folder and commit the changes.
3. In your blog’s `_config.yml` file, change the `header-img` path to the new location.
4. The `about.html` file has a different image path, so you'll want to change that one as well. In my case, I just deleted that line altogether so I would have the same background image throughout my entire site.


## Spruce Up Your About Me

Flatiron’s Blog Settings page has a small text box for your about me, but you can add as much as you want by editing the `about.html` file in your repo directly. So you don’t mess up the Jekyll styling, leave the first few lines like this:

```html
---

layout: page

title: About

header-img: "img/your-new-about-bg.png"

---
```

After that, edit the page just as you would with any `.html` file. Don’t forget to commit your changes!


## Endless Possibilities

These few changes can have a big impact on your blog, but it’s all yours. Go wild, and customize it to your heart’s content. Explore other themes, play with the styling, and see what you can come up with! GitHub’s version control makes it easy to roll back to a previous version if you make a mistake. However, for some extra security, you can always create a development branch to try out your changes before making them go live.

Whatever you do, be proud of your patch of the Internet, and let it be a reflection of your unique, magical self. You’ve got this.

