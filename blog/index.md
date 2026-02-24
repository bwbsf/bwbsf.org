---
layout: page
title: Blog
description: Updates, project notes, and announcements from the Bay Area chapter.
---
{% if site.posts and site.posts.size > 0 %}
<ul class="post-list">
  {% for post in site.posts %}
  <li class="post-list-item">
    <p class="meta-row">
      <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %-d, %Y" }}</time>
      {% if post.author %} | {{ post.author }}{% endif %}
    </p>
    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
    <p>{{ post.excerpt | strip_html | truncate: 220 }}</p>
  </li>
  {% endfor %}
</ul>
{% else %}
No posts yet. Add a file in `_posts/` named `YYYY-MM-DD-title.md` to publish the first update.
{% endif %}
