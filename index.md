---
title: ff4500
layout: index
---

## I am awake. I am alive. I am orange.

|---
| __twitter__  |  [_xs]                                               |
| __email__    |  orange@ff4500.red                                   |
| __github__   |  [ixt]		                    				      |
| __keybase__  |  [ff4500]                                            |
| __signal__   |  contact me another way to get this number           |
| __pgp__      |  [105C A1F4 AF75 DFE3 04AD C68B 7181 6DF5 3240 20E9] |
|===


---

<table>
    {% assign stuff = site.projects | sort: 'date' | reverse %}
        {% for project in stuff %}
        <tr>
            <td> <strong> {{ project.date | date: "%Y-%m-%d" }} </strong></td>
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

[_xs]: https://twitter.com/_xs
[105C A1F4 AF75 DFE3 04AD C68B 7181 6DF5 3240 20E9]: {{ site.baseurl }}/pgp.asc
[ff4500]: https://keybase.io/ff4500
[ixt]: https://github.com/ixt
