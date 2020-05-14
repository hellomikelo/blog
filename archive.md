---

layout: page
title: Archive
permalink: /archive

---
{% assign total = 0 %}
{% for post in site.posts %}
  {% assign total = total | plus: 1 %}
{% endfor %}

{% assign sorted_categories = site.categories | sort %}

<ul class="post-list">
{% for category in sorted_categories %}
  <h3>{{ category[0] }}</h3>
    {% for post in category[1] %}
    <ul class='post-list'>
    <span class="post-meta">{{ post.date | date: "%b %-d, %Y | " }}</span> 
    <a href="{{ post.url }}">{{ post.title }}</a>
    </ul>
  {% endfor %}
{% endfor %}
</ul>