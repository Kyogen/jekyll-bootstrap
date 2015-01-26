---
layout: page
title: Kyogen
---
{% include JB/setup %}

# Blog Posts
  <ul class="posts">
    {% for post in site.posts %}
      <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt }}
      <a href="{{ post.url }}">read more</a>
      </li>
    {% endfor %}
  </ul>

