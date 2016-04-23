---
layout: index
permalink: /b/
colour: orange
title: blog
---

[< back](/) - [rss feed link](/feed.xml)

watch this space

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a><div style="align:right;"> {{ post.date | date: "%Y - %m - %d" }}</div>
    </li>
  {% endfor %}
</ul>
