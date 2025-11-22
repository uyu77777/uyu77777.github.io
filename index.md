---
layout: default
---

<p class="top-message">やあやあブログだよ</p>


<ul>
  {% for post in site.posts %}
    <li>
      <h2 class="post-title">{{ post.title }}</h2>
      <p class="post-date">{{ post.date | date: "%Y-%m-%d" }}</p>
      <div class="post-content">{{ post.content }}</div>
    </li>
  {% endfor %}
</ul>


