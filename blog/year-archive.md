---
title: "Blog Archive by Year"
layout: newspaper-page
permalink: /blog/year-archive/
---

## Posts by Year

{% assign postsByYear = site.posts | group_by_exp:"post", "post.date | date: '%Y'" %}
{% for year in postsByYear %}
<h2 id="y{{ year.name }}">{{ year.name }}</h2>
<ul>
  {% for post in year.items %}
  <li>
    <a href="{{ post.url }}">{{ post.title }}</a>
    <span class="date">{{ post.date | date: "%B %d" }}</span>
  </li>
  {% endfor %}
</ul>
{% endfor %} 