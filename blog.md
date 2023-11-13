---
layout: page
title: "Blog"
permalink: /blog
published: false
---

{% assign total = 0 %}
{% for post in site.posts %}
  {% assign total = total | plus: 1 %}
{% endfor %}

{% assign total = 5 %}
<h1 class="page-heading">Recent posts ({{ total }})</h1>

<ul class="post-list">
  {% for post in site.posts limit:total %}
    <li class="post-list">      
      <h2>
        <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
      </h2>
      <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
      {{ post.excerpt | strip_html }}
      {% if post.image %}
        <a href="{{ post.url | prepend: site.baseurl }}" ><img src="{{ post.image }}" /></a>
      {% endif %}
    </li>
  {% endfor %}
</ul>