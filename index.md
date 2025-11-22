---
layout: default
title: home
---


<section class="posts">
{% assign sorted_posts = site.posts | sort: "date" | reverse %}
{% for post in sorted_posts %}

<!-- {% for post in site.posts reversed %} -->
<article class="post">
<h2 class="post-title">{{ post.title }}</h2>

<div class="post-meta">
    {{ post.date | date: "%Y-%m-%d %H:%M" }}
</div>


<div class="post-excerpt">
  {{ post.excerpt | strip_html }}
</div>


<div class="full-content" style="display:none;">
  {{ post.content | remove: post.excerpt }}
</div>

<button class="toggle">続きを読む</button>
</article>
{% endfor %}



{% if site.posts == empty %}
<p>まだ投稿がありません。最初の投稿を作成してください。</p>
{% endif %}
</section>

