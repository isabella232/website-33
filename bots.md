---
title: active bots
layout: index
permalink: /bots/
---

{% assign bots = site.bots | sort: 'date' | reverse %}
<table>
<tr>
<td> <strong> DATE </strong> </td>  
<td> Bot Name </td>  
<td> Source Tweet </td>  
</tr>
<tr> <td> Bot brief description </td> </tr>
</table>
    {% for bot in bots %}
    {% if bot.active %}
    {% if bot.published %}
<table>
<tr> 
<td> <strong> {{ bot.date | date: "%Y%m%d" }} </strong> </td>
<td> <a href="{{ bot.source }}"> {{ bot.title }}</a></td>
<td> <a href="{{ bot.twitter-source }}"> {{ bot.twitter-user }}</a></td>
</tr>
<tr> <td> {{ bot.content }} </td> </tr>
</table>
    {% endif %}
    {% endif %}
    {% endfor %}

