---
layout: post
title:  "Jekyll Bootstrap"
date:   2015-03-10 20:00:00
categories: jekyll git
---

It's been some time since my last post and my personal configuration changed a
bit. This website moved from my RaspberryPi to a "real" server, because there are
still so many things I want to try with the RPi. But this doesn't change
anything regarding the configuration I showed. So let's continue with building
a self-hosted blog!

[In my last post]({{page.previous.url}}) I talked about Jekyll, a nice alternative to Wordpress. It
works without any configuration and lets you create a blog in no-time. The
default design is very functional and minimalistic, which is sufficient to
share your thoughts with the world. But if you want to add your own style, like
custom CSS or a commenting system, it's still a lot of work.

[Jekyll Bootstrap][jb] is a really easy way to spice things up. All you have to do:
clone the Jekyll Bootstrap repository, edit the configuration and blog away! It
works just like Jekyll, with the key difference that you get shiny CSS (even
optimized for mobile browsers!), social buttons and a commenting system for
free. 

Cloning:

    git clone https://github.com/plusjade/jekyll-bootstrap.git

This gives you a repository where you can write your blogs just like you
would do with Jekyll. But on top of that, there is a file `_config.yml`:
this file let's you add all the nice stuff. You only need to configure some
variables, like a provider for the commenting system (e.g. [disqus][disqus]). Use
`jekyll serve` to try it out. Jekyll Bootstrap is Jekyll on steroids!

[jb]: http://jekyllbootstrap.com/
[disqus]: https://disqus.com/
