---
layout: default
pagination:
  enabled: true
  per_page: 5
title: Home
---

<div class="layout">
  <!-- サイドバー -->
  <aside class="sidebar">
    <h3>目次</h3>
    <ul>
      {% for post in paginator.posts %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
      {% endfor %}
    </ul>
  </aside>

  <!-- メイン記事部分 -->
  <main class="main-content">
    {% for post in paginator.posts %}
    <article class="post-card">
      <h2 class="post-title">
        <a href="{{ post.url }}">{{ post.title }}</a>
      </h2>

      <div class="post-meta">
        {{ post.date | date: "%Y-%m-%d %H:%M" }}
      </div>

      <p>{{ post.excerpt | strip_html }}</p>

      <button class="good-btn" data-id="{{ post.url }}">👍 Good</button>
    </article>
    {% endfor %}

    <!-- ページネーション -->
    <div class="pagination">
      {% if paginator.previous_page %}
      <a href="{{ paginator.previous_page_path }}">Prev</a>
      {% endif %}

      {% for page in (1..paginator.total_pages) %}
      {% if page == paginator.page %}
      <span class="current">{{ page }}</span>
      {% else %}
      <a href="{{ paginator.paginate_path | replace: ':num', page }}">{{ page }}</a>
      {% endif %}
      {% endfor %}

      {% if paginator.next_page %}
      <a href="{{ paginator.next_page_path }}">Next</a>
      {% endif %}
    </div>
  </main>
</div>

<script>
document.addEventListener("DOMContentLoaded", () => {
  document.querySelectorAll(".good-btn").forEach(button => {
    const id = button.dataset.id;
    const saved = localStorage.getItem("good-" + id) || 0;
    button.textContent = `👍 Good (${saved})`;

    button.addEventListener("click", () => {
      const updated = parseInt(localStorage.getItem("good-" + id) || 0) + 1;
      localStorage.setItem("good-" + id, updated);
      button.textContent = `👍 Good (${updated})`;
    });
  });
});
</script>
