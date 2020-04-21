---
layout: post
title:  "Vagrant boxes"
date:   2019-02-20 09:43:04 -0500
categories: devops, vagrant

---

Vagrant boxes are preconfigured images that can be downloaded from vagrant to create your own homogeneous test environment across multisystems and platforms.

## using vagrantup to get boxes

you can download vagrant boxes (image) from vagrantup.com or create your own use version control if developing your own

```
#vagrant box commands

vagrant box add <URL>
vagrant box list
vagrant box remove <name>
vagrant box update # you must destroy and recreate if you want to use it

vagrant init centos/7  # creates Vagrantfile with box centos/7

```

## creating basebox

- Virtualbox - - hdd as vmdk - install ISO - disable audio and usb - setup port forward ssh 2222 22

- create users - vagrant/vagrant and root/vagrant and setup /etc/sudoers.d/vagrant

- copy key from https://raw.githubusercontent.com/hashicorp/vagrant/master/keys/vagrant.pub authorized\_keys for vagrant user

- modify sshd AuthorizedKeysFiles %h/.ssh/authorized\_keys

- install guest tools vm

- clear up free space - `dd if=/dev/zero of=/EMPTY bs=1M rm -r /EMPTY`


on host machine - To package and add to boxes

```
 vagrant package --base <my-virtual-machine>
 vagrant box add <my-virtual-machine> package.box

```
