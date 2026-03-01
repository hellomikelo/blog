---
layout: page
title: "Blog"
permalink: /blog
published: false
---

## Recent Posts

<ul class="post-list">
  {% for post in site.posts limit:5 %}
    <li>
      <h3 class="post-list-title">
        <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      </h3>
      {% if post.description %}
        <div class="post-list-subtitle">{{ post.description }}</div>
      {% endif %}
      <div class="post-list-date">{{ post.date | date: "%Y.%m.%d" }}</div>
      {% if post.image %}
        <a href="{{ post.url | prepend: site.baseurl }}"><img src="{{ post.image }}" alt="{{ post.title }}" /></a>
      {% endif %}
    </li>
  {% endfor %}
</ul>