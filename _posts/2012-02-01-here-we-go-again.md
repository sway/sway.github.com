---
layout: post
title: "Here we go again!"
category:  
tags: [jekyll, github, development]
---

> This land is not for sale. Some day, I hope to build on it.
> <small>Dimitri Pietrovich</small>

The famous quote from a Woody Allen movie pretty much sums up my blog.
It indeed is my land, even though it is hosted on github, and one day,
probably, I really am going to build on it. But you just have to give me
time.

After some hickups and changes my site (including this blog) is up and
running. Nothing has changed from the outside (except for the design),
but inside it is completely different. First of all, I am no longer
using a "conventional" hosting. I figured out that paying some 30 EUR a
year for few megabytes of space that I don't even use is quite wasteful
and I canceled the contract. "So how is it possible that it is still
here?", you might ask. Well, since I am a geek (yep!), I use geeky
things to make that happen. More specifically, the geeky things are
called GitHub pages and jekyll.

GitHub pages is a "hosting" provided by GitHub that publishes static
content from a git repository on-line. I set up my DNS zone to serve the
GitHub page http://sway.github.com/ for egoistic.biz, so for an outsider
it is almost impossible to figure out that egoistic.biz is in fact just
a placeholder for sway.github.com.

The second thing, jekyll, is a static page generator, that is ran on the
repository upon every push. In other words, when I push my stuff to
GitHub, it generates HTML files out of Markdown/Textile files and
compiles everything together. Pretty neat, right.

This all is supported by Jekyll Bootstrap, a framework for Jekyll, that
in turn uses Twitter Bootstrap, which is a CSS/JS framework for quick
webpage creation.

So, this was a little bit of a technical mumbo jumbo, so i you don't
understand, it's fine. Soon there will be more posts, this time on more
common things. So thanks and see you then!
