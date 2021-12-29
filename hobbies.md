---
layout: page
title: Hobbies

---

{% for hobbies in site.hobbies %}

<a href="{{ hobbies.url | prepend: site.baseurl }}">
        {{ hobbies.title }}
</a>


{% endfor %}    