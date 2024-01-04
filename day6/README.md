# linux-dotnet-vodafone
## overall Revision 

### Linux basic

<img src="linux1.png">

### checking docker version 

```
ashu@ip-172-31-87-20 ~]$ docker  version 
Client:
 Version:           20.10.25
 API version:       1.41
 Go version:        go1.20.10
 Git commit:        b82b9f3
 Built:             Fri Oct 13 22:46:12 2023
 OS/Arch:           linux/amd64
 Context:           default
 Experimental:      true

Server:
 Engine:
  Version:          20.10.25
  API version:      1.41 (minimum version 1.12)
  Go version:       go1.20.10
  Git commit:       5df983c
  Built:            Fri Oct 13 22:46:59 2023
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.7.2
  GitCommit:        0cae528dd6cb557f7201036e9f43420650207b58
 runc:
  Version:          1.1.7
  GitCommit:        f19387a6bec4944c770f7668ab51c4348d9c2f38
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0

```

### what is process of app testing or deployment using docker 

<img src="cicd.png">

### linux vm to linux containers -- understanding for dotnet core app

<img src="dot.png">

### dotnet app image build and create using compose 

```
[ashu@ip-172-31-87-20 ashu-apps]$ ls
ashu-customer1-app  python-test
[ashu@ip-172-31-87-20 ashu-apps]$ cd ashu-customer1-app/
[ashu@ip-172-31-87-20 ashu-customer1-app]$ ls
docker-compose.yaml  Dockerfile  dotnet-vhost.conf  httpd.dockerfile  README.md  sample-dotnetweb-app

=====>>
[ashu@ip-172-31-87-20 ashu-customer1-app]$ docker-compose up -d --build 
[+] Building 12.7s (10/11)                                                                                 docker:default
 => [ashuapp1 internal] load build definition from Dockerfile                                                        0.0s
 => => transferring dockerfile: 546B                                                                                 0.0s
 => [ashuapp1 internal] load .dockerignore                                                                           0.0s
 => => transferring context: 2B                                                                                      0.0s
 => [ashuapp1 internal] load metadata for docker.io/redhat/ubi8:latest                                               0.1s
 => [ashuapp1 1/7] FROM docker.io/redhat/ubi8@sha256:449da7f8f2ef6285a8445a1e31af57a97b9dae5dcf009b1629c59742c89c68  0.0s
 => [ashuapp1 internal] load build context                                                                           0.1s
 => => transferring context: 8.16MB                            
```

### verify 

```
[ashu@ip-172-31-87-20 ashu-customer1-app]$ docker-compose ps
NAME      IMAGE              COMMAND                  SERVICE    CREATED          STATUS          PORTS
ashuc1    ashudotnetimg:v1   "/bin/sh -c './ashu_…"   ashuapp1   36 seconds ago   Up 35 seconds   
[ashu@ip-172-31-87-20 ashu-customer1-app]$ 
[ashu@ip-172-31-87-20 ashu-customer1-app]$ 
[ashu@ip-172-31-87-20 ashu-customer1-app]$ docker-compose images
CONTAINER           REPOSITORY          TAG                 IMAGE ID            SIZE
ashuc1              ashudotnetimg       v1                  03343783a7bf        934MB
```

