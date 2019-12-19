# Deploy Ansible
This guide will assume centos/rhel systems only.

## ansible via yum
You can install ansible with `yum -y install ansible` or you can install with python module manager `pip install ansible`.

## inventory file
To configure ansible to interact with host you need to create inventory file. If you installed by yum you can modify /etc/ansible/hosts with the desired systems hostname or ip address or create custom in ansible dir.
```
# hosts
## basic group with no addition parameters - you can also use the ip only.
[servers]
webserv.devopsbeta.com

## may be useful if users names are not the same on all systems
[altservers]
web ansible_connection=ssh ansible_ssh_user=<username> ansible_host=<ip>
```
## test systems added to host
you can use -i host if you manually created host file in your pwd. -k will prompt for passwd. -u sets the user account on system in host file.
`ansible all -m ping -u <username> -k`

## setting up hosts to use key auth
From ansible system run to generate keys
```
ssh-key-gen
```
Copy pub key to host in inventory
```
ssh-copy-id <username>@webserv.devopsbeta.com
```
retest without the -k option
```
ansible all -m ping -u <username>
```

## setting up elevated privileges on hosts or alternative that will prompt for sudo pass
echo "<username>   ALL=(ALL)       NOPASSWD: ALL" > /etc/sudoers.d/ansible
or 
on ansible system: 
you can modify your ansible.cfg by adding 
ask_sudo_pass = True
  
