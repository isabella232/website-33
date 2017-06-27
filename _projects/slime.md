---
layout: post
permalink: /slimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslime/
title: slime (x20)
date: 2017/05/15
colour: chartreuse 
type: feature length film
---

# Slimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslime

Slimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslimeslime is a compilation of the word slime created by processing videos taken from YouTube. 

<style> 
.video-container {
        position: relative;
        padding-bottom: 56.25%;
        padding-top: 30px; height: 0; overflow: hidden;
}
 
 .video-container iframe,
 .video-container object,
 .video-container embed {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
 }
</style>

<div class="video-container">
<iframe src="https://www.youtube.com/embed/c_qGsa1hZmQ" frameborder="0" width="560" height="315" allowfullscreen></iframe>
</div>

I do not to my knowledge own the video clips used. 

The following is a list of all videos used (there are repeats) in order of appearence.
<ul>
{% for line in site.data.slime-credits %}
<li> <a href="{{ line.url }}">{{ line.name }}</a></li>
{% endfor %}
</ul>
