---
layout: index
title: projects
permalink: /projects/
---

#Projects

{% for project in site.projects %}
  <h2><a href="{{ project.url }}" >
    {{ project.date }} - {{ project.title }}
  </a></h2>
{% endfor %}
