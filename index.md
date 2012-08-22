---
layout: page
title: Øystein Kjærnet
#tagline: 
---
{% include JB/setup %}

This is my blog, and here are my posts:

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>



