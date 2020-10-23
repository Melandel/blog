---
layout: default
title: Index
---
<div style="width:1px;height:20px;"></div>
{% for post in site.posts %}
<article>
  <h2><a href="{{ post.url | relative_url }}">{{ post.date | date: "%-d %B %Y" }} - {{ post.title }}</a></h2>
{{ post.excerpt }}
</article>
{% endfor %}
