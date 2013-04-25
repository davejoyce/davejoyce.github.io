---
layout: page
title: Dave's Thoughts
tagline: Current thoughts on technology
---
{% include JB/setup %}

Yet another technology blog... except these are my thoughts and observations.

## Recent Posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## Projects

A list of [my repos](https://github.com/davejoyce) will be added here.
