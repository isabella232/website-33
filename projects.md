---
layout: index
title: projects
permalink: /projects/
colour: orangered
---


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

