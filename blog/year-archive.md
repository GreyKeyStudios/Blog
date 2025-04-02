---
title: "Blog Archive by Year"
layout: page
permalink: /blog/year-archive/
---

## Posts by Year

{% for post in site.posts %}
  {% assign currentdate = post.date | date: "%Y" %}
  {% if currentdate != date %}
    {% unless forloop.first %}</ul>{% endunless %}
    <h2 id="y{{currentdate}}">{{ currentdate }}</h2>
    <ul>
    {% assign date = currentdate %}
  {% endif %}
    <li><a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%B %d" }}</li>
  {% if forloop.last %}</ul>{% endunless %}
{% endfor %} 