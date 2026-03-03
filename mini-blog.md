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
    <article class="card" data-paginated-section>
      <h2>Tech</h2>
      {% if tech_posts.size > 0 %}
      <ul class="post-list paginated-post-list" data-paginated-list data-page-size="5">
        {% for post in tech_posts %}
        <li>
          <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
          <p class="meta">{{ post.date | date: "%b %d, %Y" }}</p>
        </li>
        {% endfor %}
      </ul>
      <div class="pagination-controls" data-pagination-controls>
        <button type="button" class="pager-btn" data-prev>Previous</button>
        <p class="pagination-status" data-status></p>
        <button type="button" class="pager-btn" data-next>Next</button>
      </div>
      {% else %}
      <p>No posts yet.</p>
      {% endif %}
    </article>

    <article class="card" data-paginated-section>
      <h2>Christian</h2>
      {% if christian_posts.size > 0 %}
      <ul class="post-list paginated-post-list" data-paginated-list data-page-size="5">
        {% for post in christian_posts %}
        <li>
          <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
          <p class="meta">{{ post.date | date: "%b %d, %Y" }}</p>
        </li>
        {% endfor %}
      </ul>
      <div class="pagination-controls" data-pagination-controls>
        <button type="button" class="pager-btn" data-prev>Previous</button>
        <p class="pagination-status" data-status></p>
        <button type="button" class="pager-btn" data-next>Next</button>
      </div>
      {% else %}
      <p>No posts yet.</p>
      {% endif %}
    </article>
  </div>
</section>

<script>
  (() => {
    const sections = document.querySelectorAll("[data-paginated-section]");

    sections.forEach((section) => {
      const list = section.querySelector("[data-paginated-list]");
      const controls = section.querySelector("[data-pagination-controls]");
      if (!list || !controls) return;

      const items = Array.from(list.querySelectorAll("li"));
      const pageSize = Number(list.dataset.pageSize || 5);
      const totalPages = Math.ceil(items.length / pageSize);
      const prevBtn = controls.querySelector("[data-prev]");
      const nextBtn = controls.querySelector("[data-next]");
      const status = controls.querySelector("[data-status]");
      let currentPage = 1;

      if (items.length <= pageSize || totalPages <= 1) {
        controls.hidden = true;
        return;
      }

      const render = () => {
        const start = (currentPage - 1) * pageSize;
        const end = start + pageSize;

        items.forEach((item, idx) => {
          item.hidden = idx < start || idx >= end;
        });

        status.textContent = `Page ${currentPage} of ${totalPages}`;
        prevBtn.disabled = currentPage === 1;
        nextBtn.disabled = currentPage === totalPages;
      };

      prevBtn.addEventListener("click", () => {
        if (currentPage === 1) return;
        currentPage -= 1;
        render();
      });

      nextBtn.addEventListener("click", () => {
        if (currentPage === totalPages) return;
        currentPage += 1;
        render();
      });

      render();
    });
  })();
</script>
