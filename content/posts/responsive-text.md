---
title: Creating responsive text with SASS
date: 2018-11-23
published: true
tags: ['SASS','CSS3']
canonical_url: false
cover_image: ./images/sass-cover.png
description: "Hi everyone, now I've fixed some issues with the SSL of my blog and I'm coming back with posts.
Today I'm going to show one trick that I use to deal with some kinds of layouts making responsive text using a SASS function."
---
Hi everyone, now I've fixed some issues with the SSL of my blog and I'm coming back with posts.

Today I'm going to show one trick that I use to deal with some kinds of layouts making responsive text using a SASS function.

Most part of time I get layouts with these resolutions:

full layout : width = 1920

tablet layout : width = 768

mobile layout : width &lt;768

The problem starts when I do the full layout. The font-size, always, I mean ALWAYS has to be adjusted on "notebooks" resolutions, the 1920 layout 90% of time have fonts much bigger, so when the client see on resolutions like &gt;1300 and &lt;1600 it looks too big. So what's the solution?

Use the vw unit.

Whats I do is create a media query and use a SASS function that gets the max-width (specified by the designer) and the font-size of the 1920 layout, will be something like this:

```css
@media (min-width:1300){
    @function get-vw($target) {
        $vw-context: (1920 * 0.01) * 1px;
        @return ($target / $vw-context) * 1vw;
    }

    h1{
      font-size: get-vw(120px);
    }
}
```
Pretty simple, right? So, when you apply to some text:

![Responsive Text](./images/responsive-text.gif "Responsive Text")

This is just a trick that I use with SASS, but you can play with the vw unit as you need. This resolve my font-size problems with font scale on lower desktop resolutions. I hope it be usefull for someone, thanks for reading!