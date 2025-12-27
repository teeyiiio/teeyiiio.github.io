---
layout: page
title: 分类
permalink: /categories/
---
{% for category in site.categories %}
<h3>{{ category[0] }}</h3>
<ul>
  {% for post in category[1] %}
    <li><a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%Y-%m-%d" }}</li>
  {% endfor %}
</ul>
{% endfor %}
