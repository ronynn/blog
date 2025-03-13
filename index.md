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
  <ul class="posts-list">
    {% for post in paginator.posts %}
      <li>- <a href="{{ post.url | relative_url }}">{{ post.title }}</a> - {{ post.date | date: "%B %d, %Y" }}</li>
    {% endfor %}
  </ul>
  
  
  
  <nav class="pagination">
    {% if paginator.previous_page %}
      <a href="{{ paginator.previous_page_path | relative_url }}">&laquo; Previous</a>
    {% endif %}
    {% if paginator.next_page %}
      <a href="{{ paginator.next_page_path | relative_url }}">Next &raquo;</a>
    {% endif %}
  </nav>
</section>

<section>
  <hr/>
  <a href="{{ '/feed.xml' | relative_url }}">Subscribe via RSS Feed</a>
  <br/>
</section>