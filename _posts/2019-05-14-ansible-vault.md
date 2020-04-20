---
layout: post
title: "Ansible - Creating playbook that sets user password to vault stored variable"
date: "2019-05-14"
categories: ansible
---

This will use ansible vault that allows the storage of sensitive information in an encrypted state within playbooks.

## Step 1 - create password that is stored in ansible vault

```
mkdir -p ~/ansible/vault
touch ~/ansible/vault/N0s3kr1t
cd ~/ansible/vault

## encrypt secret file and prompts for a password 

ansible-vault encrypt N0s3kr1t

## run the following after installing passlib to create hash value of password:
pip install passlib
python -c "from passlib.hash import sha512_crypt; import getpass; print(sha512_crypt.using(rounds=5000).hash(getpass.getpass()))"

example output: $6$T7vpO60Gvn478QzE$B7UXoVThsoBwFzWvrY5yFyLHsOVgw89QPC.uB1N6DPuCHZzQnfTcyCVg1Er/B/jkmApvvQbOJTHfwEVQlEFik.

## add password to vault file 
ansible-vault edit N0s3kr1t

## N0s3kr1t file contents after edit - adjust to your requirements
userName: greplog
userPass: $6$T7vpO60Gvn478QzE$B7UXoVThsoBwFzWvrY5yFyLHsOVgw89QPC.uB1N6DPuCHZzQnfTcyCVg1Er/B/jkmApvvQbOJTHfwEVQlEFik.

```

## Step 2 - create playbook that changes user's password to stored value

```
## make changePassword.yml  - located in ~/ansible
---
- hosts: devSys
  vars_files:
  - vault/N03kr1t
  tasks:
  - name: update user password
    user: 
      name: "{{userName}}"
      update_password: always
      password: "{{userPass}}"

```

## Step 3 - run playbook

```
# Option 1 - prompt for pass at playbook run
ansible-playbook changePassword.yml --ask-vault-pass
# Option 2 - uses password file - this is stored plain txt (not nearly as secure)
ansible-playbook changePassword.yml --vault-password-file ~/.pwd

```
