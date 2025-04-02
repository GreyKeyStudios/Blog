---
title: "Blog Archive by Month"
layout: page
permalink: /blog/month-archive/
---

## Posts by Month

{% for post in site.posts %}
  {% assign currentdate = post.date | date: "%B %Y" %}
  {% if currentdate != date %}
    {% unless forloop.first %}</ul>{% endunless %}
    <h2 id="m{{post.date | date: "%Y%m"}}">{{ currentdate }}</h2>
    <ul>
    {% assign date = currentdate %}
  {% endif %}
    <li><a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%B %d" }}</li>
  {% if forloop.last %}</ul>{% endunless %}
{% endfor %} 