---
layout: default
title: Home
---


<section>
  <h2 style="font-size: 0.9rem; text-transform: uppercase; letter-spacing: 0.1em; color: var(--text-muted); margin-bottom: 2rem;">Recent Posts</h2>
  
  <ul class="posts-list">
    {% assign posts = paginator.posts | default: site.posts %}
    {% for post in posts %}
      <li class="post-item">
        <div class="post-date">
          <span class="day">{{ post.date | date: "%d" }}</span>
          <span class="month-year">{{ post.date | date: "%b %Y" }}</span>
        </div>
        
        <div class="post-info">
          <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
          <p class="post-excerpt">
            {{ post.excerpt | strip_html | truncatewords: 20 }}
          </p>
        </div>
      </li>
    {% endfor %}
  </ul>


<section style="margin-top: 4rem; text-align: center;">
  <hr style="border: 0; border-top: 1px solid var(--border-color); margin-bottom: 2rem;" />
  <a href="{{ '/feed.xml' | relative_url }}" style="font-size: 0.9rem; color: var(--text-muted);">Subscribe via RSS Feed</a>
</section>