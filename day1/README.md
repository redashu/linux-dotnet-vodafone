# linux-dotnet-vodafone

### Os component understanding 

<img src="os1.png">

### LInux as kernel 

<img src="kernel.png">

### rpm vs deb 

<img src="k1.png">

### linux vs windows based directory system 

<img src="dir.png">

### lets get started with Redhat 8 

### from windows laptop to connect remote linux based server we gonna use ssh protocol

<img src="power.png">

## lets get started with linux command line 

###  checking currently loggin username 

```
[ashu@linux-dotnet ~]$ whoami
ashu
```

### checking how many users are currently loggin

```
[ashu@linux-dotnet ~]$ who
opc      pts/0        2023-12-11 05:57 (27.58.5.47)
pooja    pts/1        2023-12-11 06:34 (103.132.30.64)
madhuri  pts/2        2023-12-11 06:34 (58.84.61.4)
anuj     pts/3        2023-12-11 06:40 (202.179.69.70)
ashu     pts/4        2023-12-11 06:43 (27.58.5.47)
vijay    pts/5        2023-12-11 06:41 (152.58.16.134)
shailesh pts/6        2023-12-11 06:44 (49.15.234.203)
vijay    pts/7        2023-12-11 06:46 (152.58.16.134)
```

## some basic commands 

### 

```
[ashu@linux-dotnet ~]$ date
Mon Dec 11 06:50:51 GMT 2023


[ashu@linux-dotnet ~]$
[ashu@linux-dotnet ~]$ cal
    December 2023
Su Mo Tu We Th Fr Sa
                1  2
 3  4  5  6  7  8  9
10 11 12 13 14 15 16
17 18 19 20 21 22 23
24 25 26 27 28 29 30
31


[ashu@linux-dotnet ~]$ cal  2023
                               2023

       January               February                 March
Su Mo Tu We Th Fr Sa   Su Mo Tu We Th Fr Sa   Su Mo Tu We Th Fr Sa
 1  2  3  4  5  6  7             1  2  3  4             1  2  3  4
 8  9 10 11 12 13 14    5  6  7  8  9 10 11    5  6  7  8  9 10 11
15 16 17 18 19 20 21   12 13 14 15 16 17 18   12 13 14 15 16 17 18
22 23 24 25 26 27 28   19 20 21 22 23 24 25   19 20 21 22 23 24 25
29 30 31               26 27 28               26 27 28 29 30 31


```

### checking particular month 

```

[ashu@linux-dotnet ~]$ cal 11  2023
    November 2023
Su Mo Tu We Th Fr Sa
          1  2  3  4
 5  6  7  8  9 10 11
12 13 14 15 16 17 18
19 20 21 22 23 24 25
26 27 28 29 30

[ashu@linux-dotnet ~]$ cal 11  2024
    November 2024
Su Mo Tu We Th Fr Sa
                1  2
 3  4  5  6  7  8  9
10 11 12 13 14 15 16
17 18 19 20 21 22 23
24 25 26 27 28 29 30
```

## Directory structure 

```
[ashu@linux-dotnet ~]$ whoami
ashu
[ashu@linux-dotnet ~]$ pwd
/home/ashu
[ashu@linux-dotnet ~]$
[ashu@linux-dotnet ~]$
[ashu@linux-dotnet ~]$ cd     /
[ashu@linux-dotnet /]$ pwd
/
[ashu@linux-dotnet /]$ ls
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
[ashu@linux-dotnet /]$
```

### creating directory under current user home directory 

```
[ashu@linux-dotnet ~]$ whoami
ashu
[ashu@linux-dotnet ~]$ pwd
/home/ashu
[ashu@linux-dotnet ~]$ mkdir hello
[ashu@linux-dotnet ~]$ ls
hello  learn  Library
[ashu@linux-dotnet ~]$ mkdir  a b c e
[ashu@linux-dotnet ~]$ ls
a  b  c  e  hello  learn  Library
[ashu@linux-dotnet ~]$
```

### removing directory 

```
[ashu@linux-dotnet home]$ pwd
/home
[ashu@linux-dotnet home]$ cd  ~
[ashu@linux-dotnet ~]$ pwd
/home/ashu
[ashu@linux-dotnet ~]$ ls
a  b  c  e  hello  learn  Library
[ashu@linux-dotnet ~]$ rmdir  hello
[ashu@linux-dotnet ~]$ ls
a  b  c  e  learn  Library
[ashu@linux-dotnet ~]$

```

### task1 solution 

```
 mkdir -p  a/b/d  a/c/e
[ashu@linux-dotnet ~]$
[ashu@linux-dotnet ~]$ ls
a  learn  Library
[ashu@linux-dotnet ~]$ ls  a
b  c
[ashu@linux-dotnet ~]$ ls  a/b
d
[ashu@linux-dotnet ~]$ ls  a/c
e
```

### removing a non empty directory 

```
[ashu@linux-dotnet ~]$ ls
a  learn  Library
[ashu@linux-dotnet ~]$ rmdir a
rmdir: failed to remove 'a': Directory not empty
[ashu@linux-dotnet ~]$
[ashu@linux-dotnet ~]$
[ashu@linux-dotnet ~]$ rm -r a
[ashu@linux-dotnet ~]$ ls
learn  Library
```

### using tree command to see entire structure of a directory 

```
 mkdir  -p   a/{b/d,c/e}
[ashu@linux-dotnet ~]$
[ashu@linux-dotnet ~]$ ls
a  learn  Library
[ashu@linux-dotnet ~]$ ls  a
b  c
[ashu@linux-dotnet ~]$ ls  a/b
d
[ashu@linux-dotnet ~]$ ls  a/c
e
[ashu@linux-dotnet ~]$
[ashu@linux-dotnet ~]$ ls
a  learn  Library
[ashu@linux-dotnet ~]$ tree a
a
├── b
│   └── d
└── c
    └── e

4 directories, 0 files
[ashu@linux-dotnet ~]$ rm -r  a
[ashu@linux-dotnet ~]$ ls
learn  Library
```




