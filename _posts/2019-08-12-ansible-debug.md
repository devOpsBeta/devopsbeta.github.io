---
layout: post
title:  "Ansible Deployment Guide"
date:   2020-08-12 09:54:04 -0500
categories: ansible
permalink: /ansible/debug
---

if you have any output you want to see while playbook runs you need to register the value in order to debug. 

Debug allows you to see what the var is set to.

```
    - name: get installed version of python
      shell: "python --version 2>&1" 
      changed_when: false
      check_mode: false
      register: _python_version

    - debug:
        var: _python_version.stdout

```
