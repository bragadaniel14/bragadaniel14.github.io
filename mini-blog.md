---
layout: default
title: Mini-Blog
permalink: /mini-blog/
---
<section class="section-block">
  <h1>Mini-Blog</h1>
  <p>
    Short notes on things I learn in technology and in Christian life. This is read-only for now.
  </p>
</section>

{% assign tech_posts = site.posts | where_exp: "post", "post.categories contains 'tech'" %}
{% assign christian_posts = site.posts | where_exp: "post", "post.categories contains 'christian'" %}

<section class="section-block">
  <div class="card-grid two-col">
    <article class="card">
      <h2>Tech</h2>
      {% if tech_posts.size > 0 %}
      <ul class="post-list">
        {% for post in tech_posts %}
        <li>
          <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
          <p class="meta">{{ post.date | date: "%b %d, %Y" }}</p>
        </li>
        {% endfor %}
      </ul>
      {% else %}
      <p>No posts yet.</p>
      {% endif %}
    </article>

    <article class="card">
      <h2>Christian</h2>
      {% if christian_posts.size > 0 %}
      <ul class="post-list">
        {% for post in christian_posts %}
        <li>
          <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
          <p class="meta">{{ post.date | date: "%b %d, %Y" }}</p>
        </li>
        {% endfor %}
      </ul>
      {% else %}
      <p>No posts yet.</p>
      {% endif %}
    </article>
  </div>
</section>
