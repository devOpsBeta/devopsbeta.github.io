---
layout: post
title:  "Ansible - Using version with when"
date:   2020-06-05 010:45:04 -0500
categories: ansible
permalink: /ansible/Ansible-VersionUsage
---

This is just an example of an use case. I used something like this to only compile custom python if version was less than.

python_version is a var set in the role.

```
- name: run me when version is less than 2.8
  when: python_version is version('2.8','<')
  shell: <<COMPILE PYTHON CODE>>


==  - equal
!=  - not equal
<   - less than
<=  - less than or equal
>   - greater than
>=  - greater than or equal



```
