---
layout: page
title: Notes
---
Collection of my short-notes on various topics. [to be updated]
{% for notes in site.notes %}

<a href="{{ notes.url | prepend: site.baseurl }}">
        {{ notes.title }}
</a>


{% endfor %}    