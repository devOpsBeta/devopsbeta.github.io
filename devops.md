---
layout: page
permalink: /devops/
title: devops
---


{% for post in site.categories.devops %}
 <li><span>{{ post.date | date_to_string }}</span> &nbsp; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
