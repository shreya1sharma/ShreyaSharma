---
layout: page
title: Notes
---
Collection of my short-notes on various topics. 
{% for notes in site.notes %}

<a href="{{ notes.url | prepend: site.baseurl }}">
        {{ notes.title }}
</a>


{% endfor %}    