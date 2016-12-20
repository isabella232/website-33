---
layout: index
title: essays
permalink: /essays/
colour: orangered
---

<table>
        {% for essay in site.essays %}
        <tr>
            <td> <strong> {{ essay.date | date_to_string }} </strong></td>
            <td> <a href="{{ site.baseurl }}{{ essay.url }}"> {{ essay.title }}</a></td>
            <td style="border-left: 0px; border-right: 0px; background-color: {{ essay.colour }};"> </td>
            <td style="border-left: 0px;"> <strong> {{ essay.type }} </strong> </td>
        </tr>
        {% endfor %}

</table>

        {% for collection in site.collections %}
            {{ collection.directory }}
        {% endfor %}
* The content on these pages change, email me if you want more info or to talk about my work
