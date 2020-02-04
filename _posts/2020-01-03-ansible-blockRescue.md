---
layout: post
title:  "Ansible Block Rescue"
date:   2020-01-29 09:43:04 -0500
categories: ansible
permalink: /ansible/blockRescue
---


What this does - playbook tries the block first. if it runs successfully the rescue never does. But if it fails it goes to rescue and run those tasks. This will help build up custom roles till you get when statements setup.


```
- name: pip install tox with offline rescue
  block: 
    - name: pip install tox
      pip: 
        name: tox

  rescue: 
    - name: transfer wheelhouse for tox
      copy: wheelhouse
      dest: /tmp/wheelhouse

    - name: pip install tox - offline
      pip:
        name: tox
        extra_args: --no-index --find-link /tmp/wheelhouse
```
