---
layout: default
---

<p style="text-align: center; font-size: 1.5em;">やあやあブログだよ</p>

<ul>
  {% for post in site.posts %}
    <li>
      <h2>{{ post.title }}</h2>
      <p>{{ post.date | date: "%Y-%m-%d" }}</p>
      <div>{{ post.content }}</div>
    </li>
  {% endfor %}
</ul>

