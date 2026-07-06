---
layout: default
title: "Projects"
---

# Projects

別リポジトリで制作した公開Webツールをまとめています。

<div class="project-grid">
{% for project in site.data.projects %}
  <div class="project-card">
    <h3>{{ project.title }}</h3>
    <p>{{ project.description }}</p>
    <a class="btn" href="{{ project.url }}" target="_blank" rel="noopener">開く</a>
  </div>
{% endfor %}
</div>
