---
title: "Blog Archive"
layout: page
permalink: /blog/archive/
---

## All Posts

{% for post in site.posts %}
  <article class="post">
    <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
    <div class="date">
      {{ post.date | date: "%B %e, %Y" }}
    </div>
    <div class="categories">
      Categories: 
      {% for category in post.categories %}
        <a href="/blog/category/{{ category }}/">{{ category }}</a>
        {% unless forloop.last %}, {% endunless %}
      {% endfor %}
    </div>
    {% if post.excerpt %}
      <div class="excerpt">
        {{ post.excerpt }}
      </div>
    {% endif %}
  </article>
{% endfor %} 