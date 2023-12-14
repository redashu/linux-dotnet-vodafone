# linux-dotnet-vodafone

### Revision 

<img src="rev.png">

### understanding concept of docker images

<img src="images.png">

### docker images 

<img src="imag1.png">

### checking docker images in linux server 

```
[ashu@docker-server ~]$ docker  images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
[ashu@docker-server ~]$ 


```

### download images from docker hub 

```
 docker  pull  openjdk 
Using default tag: latest
latest: Pulling from library/openjdk
197c1adcd755: Pull complete 
57b698b7af4b: Pull complete 
95a27dbe0150: Pull complete 
Digest: sha256:9b448de897d211c9e0ec635a485650aed6e28d4eca1efbc34940560a480b3f1f
Status: Downloaded newer image for openjdk:latest
docker.io/library/openjdk:latest
[ashu@docker-server ~]$ 
[ashu@docker-server ~]$ docker  images
REPOSITORY   TAG       IMAGE ID       CREATED         SIZE
openjdk      latest    71260f256d19   10 months ago   470MB
[ashu@docker-server ~]$ 


```

### all about images

```
docker pull oraclelinux:8.8 
8.8: Pulling from library/oraclelinux
6f1712686323: Pull complete 
Digest: sha256:88ef30e616a2a46506b3096c81e5db6dca7ee133ddb1ca155e5592a46df23a56
Status: Downloaded newer image for oraclelinux:8.8
docker.io/library/oraclelinux:8.8
[ashu@docker-server ~]$ docker images
REPOSITORY           TAG       IMAGE ID       CREATED         SIZE
python               latest    58a8f3dcd68a   6 days ago      1.02GB
oraclelinux          8.8       0f6366212b2c   7 days ago      238MB
bitnami/dotnet-sdk   latest    fe5a17dea20b   11 days ago     1.08GB
openjdk              latest    71260f256d19   10 months ago   470MB
[ashu@docker-server ~]$ 

```

### final image 

```
docker pull redhat/ubi8
Using default tag: latest
latest: Pulling from redhat/ubi8
b4e744f5f131: Pull complete 
Digest: sha256:449da7f8f2ef6285a8445a1e31af57a97b9dae5dcf009b1629c59742c89c68c3
Status: Downloaded newer image for redhat/ubi8:latest
docker.io/redhat/ubi8:latest
[ashu@docker-server ~]$ docker  images
REPOSITORY           TAG       IMAGE ID       CREATED         SIZE
python               latest    58a8f3dcd68a   6 days ago      1.02GB
oraclelinux          8.8       0f6366212b2c   7 days ago      238MB
bitnami/dotnet-sdk   latest    fe5a17dea20b   11 days ago     1.08GB
redhat/ubi8          latest    86b358a425da   6 weeks ago     205MB
openjdk              latest    71260f256d19   10 months ago   470MB
```

