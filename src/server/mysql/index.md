---
layout: home
---

# mariaDB를 설치합니다.
---

```console
hojin@DESKTOP-11LMH3B:~$ dpkg -l | grep mysql
hojin@DESKTOP-11LMH3B:~$ dpkg -l | grep mariadb
```
기본 설치가 되어 있지 않습니다.

`mariaDB-server`를 설치합니다.

```console
sudo apt -y install mariadb-server
```

설치된 페키지를 확인합니다.

```console
hojin@DESKTOP-11LMH3B:~$ dpkg -l | grep "mariadb"
ii  mariadb-client-10.3            1:10.3.22-1ubuntu1                amd64        MariaDB database client binaries
ii  mariadb-client-core-10.3       1:10.3.22-1ubuntu1                amd64        MariaDB database core client binaries
ii  mariadb-common                 1:10.3.22-1ubuntu1                all          MariaDB common metapackage
ii  mariadb-server                 1:10.3.22-1ubuntu1                all          MariaDB database server (metapackage depending on the latest version)
ii  mariadb-server-10.3            1:10.3.22-1ubuntu1                amd64        MariaDB database server binaries
ii  mariadb-server-core-10.3       1:10.3.22-1ubuntu1                amd64        MariaDB database core server files
```

`서버`와 `클라이언트`가 모두 설치가 된것을 확인할 수 있습니다.

## 프로세스 확인
---
시작여부의 프로세스를 확인해 봅니다.

```console
hojin@DESKTOP-11LMH3B:~$ ps -ef | grep mysql
hojin     5863     8  0 16:15 tty1     00:00:00 grep --color=auto mysql
```



서버를 시작합니다.
``` console
hojin@DESKTOP-11LMH3B:~$ sudo service mysql status
[sudo] password for hojin:
 * MariaDB is stopped.
``` 

```console
hojin@DESKTOP-11LMH3B:~$ sudo service mysql status
 * /usr/bin/mysqladmin  Ver 9.1 Distrib 10.3.22-MariaDB, for debian-linux-gnu on x86_64
Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Server version          10.3.22-MariaDB-1ubuntu1
Protocol version        10
Connection              Localhost via UNIX socket
UNIX socket             /var/run/mysqld/mysqld.sock
Uptime:                 15 sec

Threads: 7  Questions: 2  Slow queries: 0  Opens: 17  Flush tables: 1  Open tables: 11  Queries per second avg: 0.133
```

중지하기
```console
hojin@DESKTOP-11LMH3B:~$ sudo service mysql stop
 * Stopping MariaDB database server mysqld                                                                       [ OK ]
```

## mysql 접속하기
---

```console
hojin@DESKTOP-11LMH3B:~$ sudo mysql
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 17
Server version: 10.3.22-MariaDB-1ubuntu1 Ubuntu 20.04

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]>
```
비밀번호 기본값은 `엔터` 입니다.


