---
title: "Vagrant - VagrantFile"
date: "2019-02-21"
catagories: devops
---

VagrantFile is in ruby syntax. This is configuration that is used when vagrant creates vms. If no directory is given vagrant will mount vagrant folder as shared folder between host and container/vm .

## To setup custom sync folder

```
Vagrant.configure("2") do |config|
  config.vm.box = 'centos/7'
  # configures synced folder
  config.vm.synced_folder "./content", "/vagrant"
end 

```

## To setup multi VMs in one vagrant file

```
Vagrant.configure("2") do |config|

  config.vm.define "web" do |web|
    web.vm.box = "centos/7"
  end

  config.vm.define "db" do |db| 
    db.vm.box = "centos/7"
  end
end

```

## To create and start up VMs

cd to the folder you hace your VagrantFile in and run the following command:

```
vagrant up

```

These are really simple configuration files but can get complex fast with network / provider config. Virtualbox is the easiest to use. Libvirt seems to take the most tweaking especially with networks.
