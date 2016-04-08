---
layout: index
title: projects
permalink: /projects/
---

|---
{% for project in site.projects | sort "date" %}
| {{ project.date }} | [{{ project.title }}]({{ project.url }}) | {{ project.type }} |
{% endfor %}
|===

|---
|2016|[Liberalia]({{ site.baseurl }}/liberalia/)| performance |
|2015|[🔪🍎🍊🍋🍌🍐🍍🍴]({{ site.baseurl }}/fruit/)| performance |
|2015|[Press Any Key To Continue]({{ site.baseurl }}/any/)| installation |  
|2015|[ode to plastic and by extention cups]({{ site.baseurl }}/cups/)| webpage |  
|2014|[Sonification Of Processes & Notifications](http://hacks.youngrewiredstate.org/events/Kings%20College/sonification-of-processes-notifications-sonosocialdata-ism)| program |
|2014|[Tweet in public ](http://hacks.youngrewiredstate.org/events/Kings%20College/tweet-in-public)| twitter |
|2014|[tweet chain](https://twitter.com/_xs/status/445329208550899712)| twitter |
|2014|[Pure Colour](http://newhive.com/ixt/colourpure)| webpage |
|2014|[in c all at once](http://newhive.com/ixt/in-c-all-at-once)| webpage |
|2014|[Shepard tone](http://newhive.com/ixt/shepard)| webpage |
|2014|[_xstats twitter](https://twitter.com/_xstats)| twitter |
|2014|[_xstream twitter](https://twitter.com/_xstream)| twitter |
|2014|[animal kingdom](http://ixt.tumblr.com/tagged/animal-kingdom)| drawing |
|2013|[60//5\203](http://hacks.youngrewiredstate.org/events/YRS2013/60-5-203)| program |
|2013|[in labour of](http://ixtli.bandcamp.com/album/in-labour-of)| music |
|2011|[no ordinary trifle by psifork](http://psifork.bandcamp.com/album/no-ordinary-trifle)| music |
|===
