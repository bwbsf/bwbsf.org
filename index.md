---
layout: default
title: Home
description: Bay Area Burners Without Borders chapter homepage
---
<div class="home-shell container">
  <section class="hero" aria-labelledby="home-title">
    <div class="hero-grid">
      <div class="hero-copy">
        <p class="eyebrow">Bay Area Chapter</p>
        <h1 id="home-title">Burners Without Borders SF Bay Area</h1>
        <p>
          A local network for mutual aid, neighborhood-scale civic projects, and rapid community response.
          This site is the chapter home for updates, field notes, and opportunities to participate.
        </p>
        <ul class="pill-list" aria-label="Focus areas">
          <li>Mutual Aid</li>
          <li>Civic Projects</li>
          <li>Neighborhood Response</li>
          <li>Volunteer Coordination</li>
        </ul>
      </div>

      <aside class="hero-panel" aria-labelledby="next-up-title">
        <h2 id="next-up-title">Get Started</h2>
        <p>
          Use the blog for chapter updates, project announcements, and after-action notes. The homepage
          automatically shows recent posts.
        </p>
        <a class="button-link" href="{{ '/blog/' | relative_url }}">Read Chapter Updates</a>
      </aside>
    </div>
  </section>

  <section class="grid-cards" aria-label="Chapter focus">
    <article class="card">
      <h2>Mutual Aid Projects</h2>
      <p>
        Organize practical, local support efforts and document what is working so new volunteers can plug in quickly.
      </p>
    </article>
    <article class="card">
      <h2>Civic Collaboration</h2>
      <p>
        Partner with neighborhoods and aligned groups on visible, high-leverage projects that improve shared spaces.
      </p>
    </article>
    <article class="card">
      <h2>Field Notes and Learnings</h2>
      <p>
        Publish updates, retrospectives, and calls for support through the blog so chapter activity stays legible.
      </p>
    </article>
  </section>

  <section class="panel" aria-labelledby="recent-posts-title">
    <div class="panel-header">
      <div>
        <h2 id="recent-posts-title">Recent Blog Posts</h2>
        <p>Latest updates from the Bay Area chapter.</p>
      </div>
      <a class="button-link" href="{{ '/blog/' | relative_url }}">View All Posts</a>
    </div>

    {% if site.posts and site.posts.size > 0 %}
    <ul class="post-list">
      {% for post in site.posts limit: 5 %}
      <li class="post-list-item">
        <p class="meta-row">
          <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %-d, %Y" }}</time>
        </p>
        <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
        <p>{{ post.excerpt | strip_html | truncate: 180 }}</p>
      </li>
      {% endfor %}
    </ul>
    {% else %}
    <p>No blog posts yet. Create one in <code>_posts/</code> to populate this section.</p>
    {% endif %}
  </section>
</div>
