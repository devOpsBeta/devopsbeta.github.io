---
layout: page
permalink: /devops/
title: devops
---


{% for post in site.categories.devops %}
<li>
  <span class="post-meta">{{ post.date | date:date_format }}</span>
     <a class='post-link' href="{{ post.url | relative_url }}">
       {{ post.title | escape }}
     </a>
</li>
{% endfor %}
