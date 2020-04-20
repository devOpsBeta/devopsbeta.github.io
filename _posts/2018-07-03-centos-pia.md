---
title: "Setting up PIA VPN - CentOS7"
date: "2018-07-03"
catagories: linux
---

## Prerequisites

`yum install -y epel-release openvpn curl unzip wget`

## Verify starting public IP:

`wget -qO - icanhazip.com`

## Configure OpenVPN

```
cd /etc/openvpn
# download the PIA .ovpn files
wget https://www.privateinternetaccess.com/openvpn/openvpn.zip
# unzip file
unzip openvpn.zip
# Create cred file by inserting username on line one and password on line two:  
vi /etc/openvpn/cred.conf

# Change permissions on credential file
chmod 400 /etc/openvpn/cred.conf
# sym link desire locationConfig.ovpn to server.conf
ln -s /etc/openvpn/[locationConfig].ovpn /etc/openvpn/server.conf
# Modify server.conf file
vi server.conf
# modify the config to reflect the following
     auth-user-pass cred.conf
     auth-nocache  
# add PIA DNS servers
nameserver 209.222.18.218 >> /etc/resolv.conf
nameserver 209.222.18.222 >> /etc/resolv.conf
# Restore selinux context 
restorecon -Rv /etc/openvpn/
# start and enable at start VPN service 
# if you wish to stop VPN service use - systemctl stop openvpn@server.service
systemctl enable openvpn@server.service
systemctl start openvpn@server.service

```

## verify that public IP has changed

`wget -qO - icanhazip.com`

reboot to make sure changes are persistent and VPN is active.
