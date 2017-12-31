---
layout: post
permalink: /projects/BoaDaBoA/
title: BotADayBotAway
date: 2017/11/20
colour: "DeepPink"
link-color: "DimGray"
type: performance
---

# {{ page.title }}

For the next 12 months I will search twitter and add a bot to my twitter account that does what someone asked on twitter. 
I will likely keep using [this search](https://twitter.com/search?src=typd&q=Someone%20should%20make%20a%20bot%20that)

{% assign bots = site.bots | sort: 'date' | reverse %}
<table>
<tr>
<td> <strong> DATE </strong> </td>  
<td> Bot Name </td>  
<td> Source Tweet </td>  
</tr>
    {% for bot in bots %}
    {% if bot.project == "BoaDaBoA" %}
    {% if bot.published %}
<tr> 
<td> <strong> {{ bot.date | date: "%Y%m%d" }} </strong> </td>
<td> <a href="{{ bot.source }}"> {{ bot.title }}</a></td>
<td> <a href="{{ bot.twitter-source }}"> {{ bot.twitter-user }}</a></td>
</tr>
    {% endif %}
    {% endif %}
    {% endfor %}
</table>

---
