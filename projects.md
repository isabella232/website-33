---
layout: index
title: projects
permalink: /projects/
colour: orangered
---

## This page is a work in progress , new content may appear on old project pages as well as many being incomplete, if you want to know about any of my projects feel free to email me  

<table>
    {% assign stuff = site.projects | sort: 'date' | reverse %}
        {% for project in stuff %}
        <tr>
            <td> <strong> {{ project.date | date_to_string }} </strong></td>
            {% if project.continuous %}
            <td> C </td>
            {% else %}
            <td> S </td>
            {% endif %}
            <td> <a href="{{ site.baseurl }}{{ project.url }}"> {{ project.title }}</a></td>
            <td style="border-left: 0px; border-right: 0px; background-color: {{ project.colour }};"> </td>
            <td style="border-left: 0px;"> <strong> {{ project.type }} </strong> </td>
        </tr>
        {% endfor %}
</table>

* If the project is labeled C it is a continuous project whereas S is static

<!-- 
|---
|2013|[60//5\203](http://hacks.youngrewiredstate.org/events/YRS2013/60-5-203)| program |
|===
-->
