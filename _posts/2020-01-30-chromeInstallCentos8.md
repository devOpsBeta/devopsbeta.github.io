---
layout: post
title:  "Installing Google Chrome - Centos 8"
date:   2020-01-30 09:43:04 -0500
categories: linux
permalink: /linux/ChromeInstall-Centos8
---
```
# /etc/yum.repos.d/google-chrome.repo
[google-chrome]
name=google-chrome
baseurl=http://dl.google.com/linux/chrome/rpm/stable/x86_64
enabled=1
gpgcheck=1
gpgkey=https://dl.google.com/linux/linux_signing_key.pub


# installs google chrome
dnf install google-chrome-stable
```