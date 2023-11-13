---
layout: page
title: Archive
permalink: /archive
---

<p><hr style="width: 5%"></p>

{% include searchbar.html %} 
{% assign total = 0 %}
{% for post in site.posts %}
  {% assign total = total | plus: 1 %}
{% endfor %}

{% assign sorted_categories = site.categories | sort %}

<ul class="post-list">
{% for category in sorted_categories %}
  <h2 class="h2-post-title">{{ category[0] }}</h2>
    {% for post in category[1] %}
    <ul class='post-list'>
    	<!-- <span class="post-meta">{{ post.date | date: "%b %-d, %Y | " }}</span>  -->
      <span class="post-meta">{{ post.date | date: "%Y.%m.%d | " }}</span> 
    	<a href="{{ post.url }}">{{ post.title }}</a>
    </ul>
  {% endfor %}
{% endfor %}
</ul>