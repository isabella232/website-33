---
layout: index
permalink: /blog/
colour: lime
title: blog
---

[< back](/) - [rss feed link](/feed.xml)

watch this space

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}" style="font-size:1.25em;">{{ post.title }}</a><div style="align:right;font-size:0.7em;"> {{ post.date | date: "%Y - %m - %d" }}</div>
    </li>
  {% endfor %}
</ul>
