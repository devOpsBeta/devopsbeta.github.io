---
layout:post
title: "CentOS 7- Apache | httpd - gitea"
date: "2019-01-18"
categories: linux
---

Most guides that I see use nginx as the reverse proxy and Ubuntu as the OS. One that did cover CentOS 7 setup did so by starting out disabling selinx... what a shame since there are environments that require it. I think its sloppy to just disable it. I will be creating on that covers nginx as well

## Step 1 - installing apache and mariadb

```
## installs required services 
yum -y install httpd mariadb-server
systemctl start httpd
systemctl enable httpd
systemctl start mariadb
systemctl enable mariadb

## to set root password
mysql_secure_installation

```

## Step 2 - setting up DB

The next step is setting up DB for gitea to use: `mysql -u root -p`

```
CREATE DATABASE gitea;
CREATE USER gitea@localhost IDENTIFIED BY '<insertDesiredPasswordHere>';
GRANT ALL PRIVILEGES ON gitea.* TO gitea@localhost IDENTIFIED BY '<insertDesiredPasswordHere>';
FLUSH PRIVILEGES;

```

## Step 3 - install gitea

```
useradd -rm git
su - git
mkdir -p /home/git/gitea/{custom,data,indexers,public,log}
chmod 750 /home/git/gitea/{data,indexers,log}
cd gitea
wget -O gitea https://dl.gitea.io/gitea/1.7/gitea-1.7-linux-amd64
chmod +x gitea

```

## Step 4 - setup gitea service and reverse proxy

```
cd ~/gitea
# modify as needed. If you are following this guide no mode required
wget https://greplog.com/scratch/gitea.service
# must be ran as privilege account 
ln -s /home/git/gitea/gitea.service /etc/systemd/system/gitea.service

systemctl daemon-reload
systemctl start gitea
systemctl status gitea
systemctl enable gitea

```

### basic Apache reverse proxy - /etc/httpd/conf.d/devopsbeta.com.conf

```
<virtualhost *:80> 
  ServerName devopsbeta.com 
  ProxyPreserveHost On 
  ProxyRequests off 
  ProxyPass / http://localhost:3000/ 
  ProxyPassReverse / http://localhost:3000/ 
</virtualhost>

```

### seboolean for reverse proxy - HTTPD

sudo setsebool -P httpd\_can\_network\_connect 1 systemctl restart httpd

The first time you access site you will be able to complete gitea configuration.

## Step 5 - Setting up certbot

```
yum -y install epel-release
yum -y install certbot
certbot

```

Then follow the on screen wizard. I suggest redirecting http to https. This is only necessary if this is a public system.

## Step 6 - Setting up fail2ban

```
# from epel-release
yum -y install fail2ban


# /etc/fail2ban/filter.d/gitea.conf

echo """[Definition] failregex = .*Failed authentication attempt for .* from <host> ignoreregex =""" > /etc/fail2ban/filter.d/gitea.conf</host>

# /etc/fail2ban/jail.d/jail.local

echo """[gitea] enabled = true port = http,https filter = gitea logpath = /home/git/gitea/log/gitea.log maxretry = 10 findtime = 3600 bantime = 900 action = iptables-allports""" > /etc/fail2ban/jail.d/jail.local

systemctl restart fail2ban

```
