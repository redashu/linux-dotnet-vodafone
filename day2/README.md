### today target 

<img src="tg.png">


## linux revision 1 

<img src="rev1.png">

### linux directory structure 

<img src="rev2.png">

### sudo permission 

<img src="rev3.png">


### Concept of VM 

<img src="vm.png">

### public cloud options in market

<img src="public.png">

## lets check now the server details on centos 

```
[opc@ashu-linux-vm ~]$ hostname
ashu-linux-vm

[opc@ashu-linux-vm ~]$ whoami
opc

[opc@ashu-linux-vm ~]$ pwd
/home/opc
[opc@ashu-linux-vm ~]$ ls  /
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
[opc@ashu-linux-vm ~]$ 

```

## Deploying html sample app to centos / rhel 8 using apache httpd webapp server

### installing httpd 

```
[opc@ashu-linux-vm ~]$ sudo dnf install httpd
Failed loading plugin "osmsplugin": No module named 'librepo'
CentOS Stream 8 - AppStream                                                                               17 MB/s |  35 MB     00:02    
CentOS Stream 8 - BaseOS                                                                                  21 MB/s |  56 MB     00:02    
CentOS Stream 8 - Extras                                                                                  18 kB/s |  18 kB     00:00    
CentOS Stream 8 - Extras common packages                                                                  20 kB/s | 6.9 kB     00:00    
Extra Packages for Enterprise Linux 8 - x86_64    32% [===============                                 ] 130 kB/s | 5.1 MB     01:25 ETA



```

### verify installation and checking version 

```
[opc@ashu-linux-vm ~]$ rpm -q  httpd
httpd-2.4.37-62.module_el8+657+88b2113f.x86_64
[opc@ashu-linux-vm ~]$


[opc@ashu-linux-vm ~]$ rpm -qi  httpd
Name        : httpd
Version     : 2.4.37
Release     : 62.module_el8+657+88b2113f
Architecture: x86_64
Install Date: Tue Dec 12 06:29:15 2023
Group       : System Environment/Daemons
Size        : 4502883
License     : ASL 2.0

```

### Note: to see all the software installed 

```
 rpm  -qa 
kpatch-0.9.7-2.el8.noarch
coreutils-8.30-15.el8.x86_64
fontpackages-filesystem-1.44-22.el8.noarch
sssd-kcm-2.9.2-1.el8.x86_64
device-mapper-libs-1.02.181-9.el8.x86_64
libreport-filesystem-2.9.5-15.el8.x86_64
wget-1.19.5-11.el8.x86_64
libdb-5.3.28-42.el8_4.x86_64
abattis-cantarell-fonts-0.0.25-6.el8.noarch
```

### checking all configuration files created by httpd on linux server

```
opc@ashu-linux-vm ~]$ rpm -qc  httpd
/etc/httpd/conf.d/autoindex.conf
/etc/httpd/conf.d/userdir.conf
/etc/httpd/conf.d/welcome.conf
/etc/httpd/conf.modules.d/00-base.conf
/etc/httpd/conf.modules.d/00-dav.conf
/etc/httpd/conf.modules.d/00-lua.conf
/etc/httpd/conf.modules.d/00-mpm.conf
/etc/httpd/conf.modules.d/00-optional.conf
/etc/httpd/conf.modules.d/00-proxy.conf
/etc/httpd/conf.modules.d/00-systemd.conf
/etc/httpd/conf.modules.d/01-cgi.conf
/etc/httpd/conf/httpd.conf
/etc/httpd/conf/magic
/etc/logrotate.d/httpd
/etc/sysconfig/htcacheclean

```

### locating main config file of apache httpd server 

```
 cd  /etc/httpd/
[opc@ashu-linux-vm httpd]$ ls
conf  conf.d  conf.modules.d  logs  modules  run  state
[opc@ashu-linux-vm httpd]$ cd  conf
[opc@ashu-linux-vm conf]$ ls
httpd.conf  magic

```

### default httpd setting 

<img src="httpd.png">

### lets use sample github page 

```
[opc@ashu-linux-vm html]$ cd  ~
[opc@ashu-linux-vm ~]$ ls
[opc@ashu-linux-vm ~]$ 
[opc@ashu-linux-vm ~]$ git  clone  https://github.com/schoolofdevops/html-sample-app.git
-bash: git: command not found
[opc@ashu-linux-vm ~]$ 
[opc@ashu-linux-vm ~]$ sudo dnf  install git 
Failed loading plugin "osmsplugin": No module named 'librepo'
Last metadata expiration check: 0:32:27 ago on Tue 12 Dec 2023 06:31:55 AM GMT.
Dependencies resolved.
=========================================================================================================================================
 Package                             Architecture        Version                                            Repository              Size
=========================================================================================================================================
Installing:
 git                                 x86_64         
```

### cloning html sample code from github 

```
git  clone  https://github.com/schoolofdevops/html-sample-app.git
Cloning into 'html-sample-app'...
remote: Enumerating objects: 74, done.
remote: Counting objects: 100% (2/2), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 74 (delta 0), reused 0 (delta 0), pack-reused 72
Receiving objects: 100% (74/74), 1.38 MiB | 595.00 KiB/s, done.
Resolving deltas: 100% (5/5), done.
[opc@ashu-linux-vm ~]$ ls
html-sample-app
[opc@ashu-linux-vm ~]$ ls html-sample-app/
LICENSE.txt  README.txt  assets  elements.html  generic.html  html5up-phantom.zip  images  index.html
[opc@ashu-linux-vm ~]$ 

```

### verify code sample project

```
[opc@ashu-linux-vm ~]$ ls
html-sample-app  project-html-website
[opc@ashu-linux-vm ~]$ ls  html-sample-app/
LICENSE.txt  README.txt  assets  elements.html  generic.html  html5up-phantom.zip  images  index.html
[opc@ashu-linux-vm ~]$ 
[opc@ashu-linux-vm ~]$ 
[opc@ashu-linux-vm ~]$ 
[opc@ashu-linux-vm ~]$ ls  project-html-website/
LICENSE  README.md  SECURITY.md  css  fonts  img  index.html
[opc@ashu-linux-vm ~]$ 
[opc@ashu-linux-vm ~]$ 

```

### copy code to /var/www/html/

```
[opc@ashu-linux-vm ~]$ ls
html-sample-app  project-html-website
[opc@ashu-linux-vm ~]$ ls  html-sample-app/
LICENSE.txt  README.txt  assets  elements.html  generic.html  html5up-phantom.zip  images  index.html
[opc@ashu-linux-vm ~]$ 
[opc@ashu-linux-vm ~]$ 
[opc@ashu-linux-vm ~]$ sudo  cp -rf  html-sample-app/*   /var/www/html/
[opc@ashu-linux-vm ~]$ cd  /var/www/html/
[opc@ashu-linux-vm html]$ ls
LICENSE.txt  README.txt  assets  elements.html  generic.html  html5up-phantom.zip  images  index.html
[opc@ashu-linux-vm html]$ 


```

### starting service of httpd server

```
sudo  systemctl  start httpd
[opc@ashu-linux-vm ~]$ sudo  systemctl  status httpd
● httpd.service - The Apache HTTP Server
   Loaded: loaded (/usr/lib/systemd/system/httpd.service; disabled; vendor preset: disabled)
   Active: active (running) since Tue 2023-12-12 07:19:55 GMT; 3s ago
     Docs: man:httpd.service(8)
 Main PID: 34359 (httpd)
   Status: "Started, listening on: port 80"
    Tasks: 213 (limit: 22608)
   Memory: 17.5M
   CGroup: /system.slice/httpd.service
           ├─34359 /usr/sbin/httpd -DFOREGROUND
           ├─34360 /usr/sbin/httpd -DFOREGROUND
           ├─34361 /usr/sbin/httpd -DFOREGROUND
           ├─34362 /usr/sbin/httpd -DFOREGROUND
           └─34363 /usr/sbin/httpd -DFOREGROUND

Dec 12 07:19:55 ashu-linux-vm systemd[1]: Starting The Apache HTTP Server...
Dec 12 07:19:55 ashu-linux-vm systemd[1]: Started The Apache HTTP Server.
Dec 12 07:19:55 ashu-linux-vm httpd[34359]: Server configured, listening on: port 80
[opc@ashu-linux-vm ~]$ 

```

### optional step -- to set auto-start on server rebot 

```
sudo  systemctl enable  httpd
Created symlink /etc/systemd/system/multi-user.target.wants/httpd.service → /usr/lib/systemd/system/httpd.service.
[opc@ashu-linux-vm ~]$ 

```

### page is not loading due to OS / server internal firewall 

<img src="firewall.png">

### checking firewalld

```
sudo systemctl status  firewalld
● firewalld.service - firewalld - dynamic firewall daemon
   Loaded: loaded (/usr/lib/systemd/system/firewalld.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2023-12-12 06:07:12 GMT; 1h 25min ago
     Docs: man:firewalld(1)
 Main PID: 1069 (firewalld)
    Tasks: 2 (limit: 22608)
   Memory: 29.6M

```

### checking rules and allow http connection 

```

[opc@ashu-linux-vm ~]$ sudo  firewall-cmd  --list-service
cockpit dhcpv6-client ssh
[opc@ashu-linux-vm ~]$ 
[opc@ashu-linux-vm ~]$ sudo  firewall-cmd  --add-service=http 
success
[opc@ashu-linux-vm ~]$ sudo  firewall-cmd  --add-service=http --permanent 
success
[opc@ashu-linux-vm ~]$ sudo  firewall-cmd  --list-service
cockpit dhcpv6-client http ssh
[opc@ashu-linux-vm ~]$ 

```

## COncept of VirtualHosting 

<img src="vhost.png">

### More closure 

<img src="vhost1.png">

### creating virtualhost 

```
[opc@ashu-linux-vm conf.d]$ pwd
/etc/httpd/conf.d
```

### default.conf 

```
cat  default.conf 
<virtualhost *:80>

</virtualhost>

```

### adding two virutalhost 

```
[opc@ashu-linux-vm conf.d]$ ls
README  ashu-adhoc.conf  ashu-delvex.conf  autoindex.conf  default.conf  userdir.conf  welcome.conf
[opc@ashu-linux-vm conf.d]$ cat  default.conf 
<virtualhost *:80>
	servername 152.67.9.194
	documentroot /var/www/html/
</virtualhost>

[opc@ashu-linux-vm conf.d]$ 
[opc@ashu-linux-vm conf.d]$ cat  ashu-adhoc.conf 
<virtualhost *:80>
	servername ashu.adhocnet.org
	documentroot /var/www/adhoc/
</virtualhost>


[opc@ashu-linux-vm conf.d]$ 
[opc@ashu-linux-vm conf.d]$ 
[opc@ashu-linux-vm conf.d]$ cat  ashu-delvex.conf 
<virtualhost *:80>
	servername ashu.delvex.io
	documentroot /var/www/delvex/
</virtualhost>


[opc@ashu-linux-vm conf.d]$ cd  /var/www/
[opc@ashu-linux-vm www]$ ls
cgi-bin  html
[opc@ashu-linux-vm www]$ sudo mkdir  adhoc delvex
[opc@ashu-linux-vm www]$ ls
adhoc  cgi-bin  delvex  html

[opc@ashu-linux-vm www]$ cd  adhoc/
[opc@ashu-linux-vm adhoc]$ ls
[opc@ashu-linux-vm adhoc]$ sudo vim  index.html 
[opc@ashu-linux-vm adhoc]$ cat index.html 
<h1> Hello adhoc </h1>

[opc@ashu-linux-vm adhoc]$ cd ../delvex/
[opc@ashu-linux-vm delvex]$ sudo vim  index.html 
[opc@ashu-linux-vm delvex]$ cat index.html 
<h1> hello Delvex welcome to linux vhosting </h1>
[opc@ashu-linux-vm delvex]$ 

```


### incase we want to test config changes before restarting service

```
 httpd  -t
Syntax OK

======>> OR 
[opc@ashu-linux-vm conf.d]$ apachectl configtest
Syntax OK
[opc@ashu-linux-vm conf.d]$ 



```

### lets restart service

```
[opc@ashu-linux-vm conf.d]$ sudo systemctl restart httpd
[opc@ashu-linux-vm conf.d]$ sudo systemctl status httpd
● httpd.service - The Apache HTTP Server
   Loaded: loaded (/usr/lib/systemd/system/httpd.service; enabled; vendor preset: disabled)
   Active: active (running) since Tue 2023-12-12 09:21:27 GMT; 4s ago
     Docs: man:httpd.service(8)
 Main PID: 36024 (httpd)
   Status: "Started, listening on: port 80"
    Tasks: 213 (limit: 22608)
   Memory: 17.6M
   CGroup: /system.slice/httpd.service
           ├─36024 /usr/sbin/httpd -DFOREGROUND

```

## Info about .net -- .net core 

<img src="sdk.png">




