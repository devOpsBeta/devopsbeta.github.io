---
layout: page
permalink: /linux/
title: linux
---
{% for post in site.categories.linux %}
 <li>
   <span class="post-meta">{{ post.date | date:date_format }}</span>
   <h3> 
      <a class='post-link' href="{{ post.url | relative_url }}">
        {{ post.title | escape }}
      </a>
   </h3>
 </li>
{% endfor %}



