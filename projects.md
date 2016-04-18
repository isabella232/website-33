---
layout: index
title: projects
permalink: /projects/
colour: yellow
---

{% assign stuff = site.projects | sort: 'date' | reverse %}
{% for project in stuff %}
| {{ project.date | date_to_string }} | [{{ project.title }}]({{ project.url }}){: style="background-color: {{ project.colour }}"} | {{ project.type }} |
{% endfor %}

---

|---
|2013|[60//5\203](http://hacks.youngrewiredstate.org/events/YRS2013/60-5-203)| program |
|2013|[in labour of](http://ixtli.bandcamp.com/album/in-labour-of)| music |
|2011|[no ordinary trifle by psifork](http://psifork.bandcamp.com/album/no-ordinary-trifle)| music |
|===
