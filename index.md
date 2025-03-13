---
layout: default
title: Home
---

<section>
  <h2>Pages</h2>
  <ul>
    {% for page in site.pages %}
      {% if page.title and page.url != '/' %}
        <li><a href="{{ page.url | relative_url }}">{{ page.title }}</a></li>
      {% endif %}
    {% endfor %}
  </ul>
</section>
  
  
  
<section>
  <h2>Blog Posts</h2>
  <ul>
    {% for post in site.posts %}
      <li>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a> - {{ post.date | date: "%B %d, %Y" }}<br>
        Tags: 
        {% for tag in post.tags %}
          <a href="{{ '/tags/' | append: tag | relative_url }}">{{ tag }}</a>{% unless forloop.last %}, {% endunless %}
        {% endfor %}
      </li>
    {% endfor %}
  </ul>
</section>