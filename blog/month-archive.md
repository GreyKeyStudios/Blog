---
title: "Blog Archive by Month"
layout: newspaper-page
permalink: /blog/month-archive/
---

## Posts by Month

{% assign postsByMonth = site.posts | group_by_exp:"post", "post.date | date: '%B %Y'" %}
{% for month in postsByMonth %}
<h2 id="m{{ month.name | date: '%Y%m' }}">{{ month.name }}</h2>
<ul>
  {% for post in month.items %}
  <li>
    <a href="{{ post.url }}">{{ post.title }}</a>
    <span class="date">{{ post.date | date: "%B %d" }}</span>
  </li>
  {% endfor %}
</ul>
{% endfor %} 