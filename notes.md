---
layout: index
title: essays
permalink: /notes/
colour: orangered
---

<table>
        {% for note in site.notes %}
        <tr>
            <td> <strong> {{ note.date | date_to_string }} </strong></td>
            <td> <a href="{{ site.baseurl }}{{ note.url }}"> {{ note.title }}</a></td>
            <td style="border-left: 0px; border-right: 0px; background-color: {{ note.colour }};"> </td>
            <td style="border-left: 0px;"> <strong> {{ note.type }} </strong> </td>
        </tr>
        {% endfor %}

</table>

