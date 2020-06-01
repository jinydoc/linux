---
layout: home
---

# sqlite3 설치
---

```console
hojin@DESKTOP-11LMH3B:~$ dpkg -l | grep sql
ii  libsqlite3-0:amd64             3.31.1-4                          amd64        SQLite 3 shared library
```
기본적으로 sqlite3 라이브러리만 설치가 되어 있습니다.

sqlite3를 설치합니다.

```console
sudo apt -y install sqlite3
```

|실습결과|
```console
hojin@DESKTOP-11LMH3B:~$ sudo apt -y install sqlite3
[sudo] password for hojin:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  sqlite3-doc
The following NEW packages will be installed:
  sqlite3
0 upgraded, 1 newly installed, 0 to remove and 32 not upgraded.
Need to get 860 kB of archives.
After this operation, 2802 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu focal/main amd64 sqlite3 amd64 3.31.1-4 [860 kB]
Fetched 860 kB in 6s (152 kB/s)
Selecting previously unselected package sqlite3.
(Reading database ... 36951 files and directories currently installed.)
Preparing to unpack .../sqlite3_3.31.1-4_amd64.deb ...
Unpacking sqlite3 (3.31.1-4) ...
Setting up sqlite3 (3.31.1-4) ...
Processing triggers for man-db (2.9.1-1) ...
```

설치가 완료되었습니다. 페키지 목록에서 설치를 확인합니다.


```console
hojin@DESKTOP-11LMH3B:~$ dpkg -l | grep sql
ii  libsqlite3-0:amd64             3.31.1-4                          amd64        SQLite 3 shared library
ii  sqlite3                        3.31.1-4                          amd64        Command line interface for SQLite 3
```

## 실행해 보기
---

```console
hojin@DESKTOP-11LMH3B:~$ sqlite3
SQLite version 3.31.1 2020-01-27 19:55:54
Enter ".help" for usage hints.
Connected to a transient in-memory database.
Use ".open FILENAME" to reopen on a persistent database.
sqlite>
```

나가기
```
sqlite> .quit
```
