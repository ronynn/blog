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

  <nav class="pagination" style="display: flex; justify-content: flex-end; margin-top: 3rem;">
    {% if paginator and paginator.previous_page %}
      <a href="{{ paginator.previous_page_path | relative_url }}" style="margin-right: 1rem;">&larr; Newer</a>
    {% endif %}
    
    <a href="/archive" style="font-weight: bold; text-transform: uppercase; font-size: 0.8rem; color: var(--text-main);">All Posts &rarr;</a>

    {% if paginator and paginator.next_page %}
      <a href="{{ paginator.next_page_path | relative_url }}" style="margin-left: 1rem;">Older &rarr;</a>
    {% endif %}
  </nav>
</section>

<section style="margin-top: 4rem; text-align: center;">
  <hr style="border: 0; border-top: 1px solid var(--border-color); margin-bottom: 2rem;" />
  <a href="{{ '/feed.xml' | relative_url }}" style="font-size: 0.9rem; color: var(--text-muted);">Subscribe via RSS Feed</a>
</section>