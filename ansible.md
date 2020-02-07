---
layout: page
permalink: /ansible/
title: ansible
---


{% for post in site.categories.ansible %}
 <li><span>{{ post.date | date_to_string }}</span> &nbsp; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
