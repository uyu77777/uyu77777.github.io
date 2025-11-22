---
layout: default
title: home
---


<section class="posts">
{% for post in site.posts reversed %}
<article class="post">
<h2 class="post-title">{{ post.title }}</h2>
<div class="post-meta">{{ post.date | date: "%Y-%m-%d" }} ・ {{ post.categories | join: ", " }}</div>


<div class="post-excerpt">{{ post.excerpt | strip_html | truncate: 300 }}</div>


<button class="toggle">続きを読む</button>


<div class="full-content" style="display:none;">{{ post.content }}</div>
</article>
{% endfor %}


{% if site.posts == empty %}
<p>まだ投稿がありません。最初の投稿を作成してください。</p>
{% endif %}
</section>

