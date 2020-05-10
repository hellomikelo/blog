---

layout: page
title: "Archive"
permalink: /archive

---
{% assign total = 0 %}
{% for post in site.posts %}
  {% assign total = total | plus: 1 %}
{% endfor %}

<ul class="category">
{% for category in site.categories %}
  <h1>{{ category[0] }}</h1>
    {% for post in category[1] %}
    <ul class='post-list'>
    <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>     
    <a href="{{ post.url }}">{{ post.title }}</a>
    </ul>
  {% endfor %}
{% endfor %}
</ul>