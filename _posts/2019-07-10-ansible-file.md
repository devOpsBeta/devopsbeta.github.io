---
layout: post
title:  "Ansible File Module"
date:   2019-07-10 09:43:04 -0500
categories: ansible
permalink: /ansible/filemod
---

Here are some examples of using copy and file module. I will be adding more as time goes on.

```
# copy module
- name: Copy file with owner and permissions
  copy:
    src: /srv/myfiles/foo.conf
    dest: /etc/foo.conf
    owner: foo
    group: foo
    mode: '0644'
    #backup: yes
```

```
# file module - ansible

- name: Create a symbolic link
  file:
    src: /file/to/link/to
    dest: /path/to/symlink
    owner: foo
    group: foo
    state: link

- name: Create a directory if it does not exist or check permission and ownership
  file:
    path: /etc/some_directory
    state: directory
    mode: '0755'
    owner: root
    group: root

``` 
