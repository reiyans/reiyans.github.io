---
layout: default
title: "Blog"
---

<div class="blog-header">
  <h1>Blog</h1>
  <button id="new-post-btn" class="new-post-btn" type="button" title="新しい記事を作成" hidden>+</button>
</div>

<ul class="blog-list">
{% for post in site.posts %}
  <li>
    <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
  </li>
{% endfor %}
</ul>

<script>
(function () {
  var params = new URLSearchParams(window.location.search);
  if (params.get('new') !== '1') return;

  var btn = document.getElementById('new-post-btn');
  btn.hidden = false;

  btn.addEventListener('click', function () {
    var now = new Date();
    var pad = function (n) { return String(n).padStart(2, '0'); };
    var dateOnly = now.getFullYear() + '-' + pad(now.getMonth() + 1) + '-' + pad(now.getDate());
    var dateTime = dateOnly + ' ' + pad(now.getHours()) + ':' + pad(now.getMinutes()) + ':' + pad(now.getSeconds()) + ' +0900';

    var filename = '_posts/' + dateOnly + '-new-post.md';
    var template = [
      '---',
      'layout: default',
      'title: "新しい記事"',
      'date: ' + dateTime,
      'categories: []',
      '---',
      '',
      'ここに本文を書いてください。',
      ''
    ].join('\n');

    var url = 'https://github.com/reiyans/reiyans.github.io/new/main'
      + '?filename=' + encodeURIComponent(filename)
      + '&value=' + encodeURIComponent(template);

    window.open(url, '_blank');
  });
})();
</script>
