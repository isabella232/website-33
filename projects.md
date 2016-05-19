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
            <td> <a href="{{ site.baseurl }}{{ project.url }}"> {{ project.title }}</a></td>
            <td style="border-left: 0px; border-right: 0px; background-color: {{ project.colour }};"> </td>
            <td style="border-left: 0px;"> <strong> {{ project.type }} </strong> </td>
        </tr>
        {% endfor %}
</table>

<!-- 
|---
|2013|[60//5\203](http://hacks.youngrewiredstate.org/events/YRS2013/60-5-203)| program |
|2013|[in labour of](http://ixtli.bandcamp.com/album/in-labour-of)| music |
|2011|[no ordinary trifle by psifork](http://psifork.bandcamp.com/album/no-ordinary-trifle)| music |
|===
-->

---
