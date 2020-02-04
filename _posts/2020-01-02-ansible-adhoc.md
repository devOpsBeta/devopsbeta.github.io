---
layout: post
title:  "Ansible adhoc guide"
date:   2020-01-29 09:43:04 -0500
categories: ansible
permalink: /ansible/adhoc
---

```
# adhoc examples

ansible <system or group in inventory> -i <hostFile> -m <moduleYouWant> -a <module options>

note -i is not needed if you are using /etc/ansible/hosts

# check uptime
ansible all -i hosts -m raw -a 'uptime'

# check partition utilization
ansible all -i hosts -m raw -a 'df -h' | grep -C 10 9.%


# check if any rhel/centos server needs reboot
ansible servers -i hosts -m shell -a "needs-restarting ; echo $?"


# check for high utitlized partitions 
ansible servers -i hosts -m shell -a "df -h | egrep '[8-9][0-9]%' 2>&1"

```