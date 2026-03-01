---
layout: page
title: Archive
permalink: /archive
---

{% include searchbar.html %}

{% assign sorted_categories = site.categories | sort %}

<div class="archive-list">
{% for category in sorted_categories %}
  <h2 class="h2-post-title">{{ category[0] }}</h2>
  <ul class="post-list archive-posts">
    {% for post in category[1] %}
      <li>
        <span class="post-meta">{{ post.date | date: "%Y.%m.%d" }}</span>
        <a href="{{ post.url }}">{{ post.title }}</a>
      </li>
    {% endfor %}
  </ul>
{% endfor %}
</div>