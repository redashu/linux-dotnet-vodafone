# linux-dotnet-vodafone

### Dotnet app with Loadbalancer case 

## we are having 2 server lets do the same thing in both server 

# server 1 

### Install dotnet and httpd -- RHEL 8/9 

```
 [ec2-user@server1 ~]$ pwd
/home/ec2-user
[ec2-user@server1 ~]$ sudo -i
[root@server1 ~]# whoami
root
[root@server1 ~]# cd  /opt/
[root@server1 opt]# ls
[root@server1 opt]# git clone https://github.com/redashu/ashu-customer1-app.git
Cloning into 'ashu-customer1-app'...
remote: Enumerating objects: 122, done.
remote: Counting objects: 100% (122/122), done.
remote: Compressing objects: 100% (78/78), done.
remote: Total 122 (delta 41), reused 108 (delta 35), pack-reused 0
Receiving objects: 100% (122/122), 863.23 KiB | 20.55 MiB/s, done.
Resolving deltas: 100% (41/41), done.
[root@server1 opt]# 


```

### checking app code 

```
[root@server1 sample-dotnetweb-app]# pwd
/opt/ashu-customer1-app/sample-dotnetweb-app
[root@server1 sample-dotnetweb-app]# ls
appsettings.Development.json  ashu-webapp.csproj  Models  Program.cs  README.md  wwwroot
appsettings.json              Controllers         obj     Properties  Views
[root@server1 sample-dotnetweb-app]# 


```

### Disable firewalld in local rhel server
```
sudo systemctl disable --now  firewalld
```

### how to check ports used by linux server

```
[root@server1 system]# netstat -nlpt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 127.0.0.1:81            0.0.0.0:*               LISTEN      669/ashu-webapp     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1032/sshd: /usr/sbi 
tcp        0      0 0.0.0.0:82              0.0.0.0:*               LISTEN      2624/ashu-webapp    
tcp6       0      0 ::1:81                  :::*                    LISTEN      669/ashu-webapp     
tcp6       0      0 :::22                   :::*                    LISTEN      1032/sshd: /usr/sbi 
tcp6       0      0 :::80                   :::*                    LISTEN      2322/httpd          
[root@server1 system]# 
[root@server1 system]# 
[root@server1 system]# ss -nlpt
State       Recv-Q      Send-Q           Local Address:Port           Peer Address:Port     Process                                      
LISTEN      0           512                  127.0.0.1:81                  0.0.0.0:*         users:(("ashu-webapp",pid=669,fd=266))      
LISTEN      0           128                    0.0.0.0:22                  0.0.0.0:*         users:(("sshd",pid=1032,fd=3))              
LISTEN      0           512                    0.0.0.0:82                  0.0.0.0:*         users:(("ashu-webapp",pid=2624,fd=266))     
LISTEN      0           512                      [::1]:81                     [::]:*         users:(("ashu-webapp",pid=669,fd=267))      
LISTEN      0           128                       [::]:22                     [::]:*         users:(("sshd",pid=1032,fd=4))              
LISTEN      0           511                          *:80                        *:*         users:(("httpd",pid=2326,fd=4),("httpd",pid=2325,fd=4),("httpd",pid=2324,fd=4),("httpd",pid=2322,fd=4))

```

### history 

```
1  hostnamectl set-hostname server2
    2   dnf install dotnet-sdk-8.0.x86_64   httpd -y
    3  ls
    4  dnf install git -y
    5  cd /opt/
    6  ls
    7  git clone https://github.com/redashu/ashu-customer1-app.git
    8  cd ashu-customer1-app/
    9  ls
   10  cd sample-dotnetweb-app/
   11  ls
   12  dotnet build
   13  dotnet publish
   14  vim /etc/systemd/system/ashuapp.service
   15  dnf install vim -y
   16  vim /etc/systemd/system/ashuapp.service
   17  systemctl start ashu-webapp.csproj 
   18  systemctl start ashu-webapp.service
   19  systemctl start ashuapp.service
   20  systemctl status ashuapp.service
   21  cd  /etc/httpd/conf.d/
   22  ls
   23  vim ashu.conf
   24  httpd -t
   25  systemctl restart httpd
   26  ls
   27  cat  ashu.conf 

```

### content in side ashuapp.service

```
[Unit]
Description=ashu ASP.NET Core Application

[Service]
WorkingDirectory=/opt/ashu-customer1-app/sample-dotnetweb-app/bin/Release/net8.0/publish/
ExecStart=/opt/ashu-customer1-app/sample-dotnetweb-app/bin/Release/net8.0/publish/ashu-webapp  --urls=http://localhost:81
Restart=always
RestartSec=10
SyslogIdentifier=your-app
User=root
Environment=ASPNETCORE_ENVIRONMENT=Production

[Install]
WantedBy=multi-user.target
```

### content ashu.conf

```
<virtualhost *:80>
#  we wanto run dotnet app using this vhost 
	servername vodafone1.delvex.io
	ProxyPass /  http://localhost:81/
	ProxyPassReverse / http://localhost:81/
	ErrorLog /var/log/httpd/ashuapp_error.log
 	CustomLog /var/log/httpd/ashuapp_access.log combined
</virtualhost>

```

