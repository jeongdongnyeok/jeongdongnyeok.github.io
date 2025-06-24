---
layout: home
---

<!-- 최신 포스트 2개 -->
<h2>📝 Recent Posts</h2>
<ul>
  {% for post in site.posts limit:2 %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <span>{{ post.date | date: "%Y-%m-%d" }}</span>
    </li>
  {% endfor %}
</ul>

<!-- 카테고리 폴더 리스트 -->
<h2>🗂️ Category</h2>
<ul>
  {% assign categories = site.categories | sort %}
  {% for category in categories %}
    <li>
      <a href="/categories/#{{ category[0] }}">{{ category[0] }} ({{ category[1].size }})</a>
    </li>
  {% endfor %}
</ul>
