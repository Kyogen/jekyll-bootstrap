---
layout: post
title:  "Blogging with Jekyll"
date:   2014-09-09 22:00:00
categories: jekyll installation
---

There a many ways to maintain a blog, like Wordpress. This is probably the most
popular blogging infrastructure, and I was able to get it running on my Pi
without any hassle. But still, it just seems overkill to me. Which brings me to
[Jekyll][jekyll].

Jekyll is a helper designed for easy deployment of static websites. What does
that mean? A static website is pure HTML: no server-side scripting like PHP,
which creates dynamic websites 'on the fly'. Take shopping websites for
example: they are created by scripts, customizing the content for each user.

Such functionality is not really necessary for a blog. What you want to do is
writing some content and publish that to the internet, which means creating
HTML files. But writing HTML-formatted text is really cumbersome. Therefore,
Jekyll helps you with that. All you need to do is writing your blog posts in
pure text files, together with some [Markdown][md] highlighting, let Jekyll parse these
files and voila: Jekyll spews out HTML! You can then take these files and let
them be served by a [webserver daemon]({{page.previous.url}}).

Jekyll is written in Ruby, a programming language which provides its own
package manager ('gem'). You can install it systemwide:

    sudo gem install --no-user-install --no-rdoc --no-ri jekyll

If Jekyll complains that it needs a javascript runtime:

    sudo pacman -S nodejs

To get started, type

    jekyll new test

This will create a new directory 'test', which contains some subdirectories:

    |-- test/
    |   |-- _config.yml
    |   |-- css/
    |   |-- index.html
    |   |-- _layouts/
    |   |-- _posts/

This is the starting point for your blog. The `_posts` folder holds all your
blog posts as simple text files. You can let Jekyll generate the HTML pages and
serve them on localhost for testing:

    jekyll serve 

Just point your browser to localhost on port 4000 and you will see the example
content created by `jekyll new`. Start your blogging by editing the file in
`_posts`, then customize 'index.html', and so on.

There are many advantages with this approach:

* you can put the folder under version control (i.e. git)
* you can put normal HTML files into the folder and let them be parsed by
  Jekyll too (e.g. the index.html file in the test folder)
* no cumbersome HTML formatting; just write your posts as simple text files and
  use Mardown for formatting
* you can use some scripting (see the example posts created above)

This blog is built with Jekyll and until now I am very pleased with it.

[pi]: http://www.raspberrypi.org/
[jekyll]: http://jekyllrb.com/
[wiki]: https://wiki.archlinux.org/
[md]: http://daringfireball.net/projects/markdown/
