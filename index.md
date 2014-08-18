---
layout: page
title: Kyogen
---
{% include JB/setup %}

# About myself

I mainly deal in all things Linux: programming in C and Bash (and a little bit
C++). My Linux distribution of choice is
[Archlinux][arch]. It's rolling release and very
customizable. Give it a try!  With this blog I want to share some of my
experiences in computing. I'm in no way an expert, but I considered blogs like
this always to be very helpful.
 
# Blog Posts
  <ul class="posts">
    {% for post in site.posts %}
      <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt }}
      <a href="{{ post.url }}">read more</a>
      </li>
    {% endfor %}
  </ul>

[arch]:https://www.archlinux.org/
