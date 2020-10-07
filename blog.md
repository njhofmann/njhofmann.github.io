---
layout: default
title:  Blog
permalink: /blog/
---

# {{ page.title }}

<ul>
  {% for post in site.posts %}
      <h2>{{ post.date |  date_to_string: "ordinal", "US" }} - <a href="{{ post.url }}">{{ post.title }}</a></h2>
      {{ post.excerpt }}
  {% endfor %}
</ul>

