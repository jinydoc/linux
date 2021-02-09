---
layout: home
---

# 시작/정지/상태/활성화
---
서버를 실행, 정지, 재시동, 상태를 확인할 수 있습니다.

<br>

## systemctl
---
Apt 명령어로 설치를 할 경우 `/etc/system/system`에 `서비스이름.service` 또는 `서비스이름.socket`으로 등록된다.

```
$ sudo systemctl start 서비스 이름
```

* start : 시작
* stop : 종료
* restart : 재시작
* status : 상태
* enable
* disable

<br>

## 상시 기동
---
서버를 재시작할 경우 매번 마리아DB 데몬을 다시 실행해 주어야 합니다.
enable 명령을 이용하면 서버가 재부팅시 자동으로 마리아DB를 자동으로 데몬을 실행해 줍니다.

```
systemctl enable 서비스이름
```

<br>

## 상태확인
---
마리아DB 데몬의 실행 상태를 확인합니다.

```
hojin@hojin:~$ sudo systemstl status mariadb
sudo: systemstl: command not found
hojin@hojin:~$ sudo systemctl status mariadb
● mariadb.service - MariaDB 10.5.8 database server
     Loaded: loaded (/lib/systemd/system/mariadb.service; enabled; vendor preset: enabled)
    Drop-In: /etc/systemd/system/mariadb.service.d
             └─migrated-from-my.cnf-settings.conf
     Active: active (running) since Fri 2021-01-01 15:32:16 KST; 16min ago
       Docs: man:mariadbd(8)
             https://mariadb.com/kb/en/library/systemd/
   Main PID: 4815 (mariadbd)
     Status: "Taking your SQL requests now..."
      Tasks: 10 (limit: 1074)
     Memory: 68.0M
     CGroup: /system.slice/mariadb.service
             └─4815 /usr/sbin/mariadbd
```

<br>

## 서버 정지하기
---
마리아DB 데몬 실행을 중지 합니다.

```
$ sudo systemctl stop mariadb
```

<br>

## 서버 실행하기
---
마리아DB 데몬을 실행합니다.

```
$ sudo systemctl start mariadb
```

또는

```
$ sudo service mysql start
```

<br>

## 항상 실행하기
---
MariaDB를 새로이 설치할때 또는 systemctl 명령을 통하여 서버를 실행할 수 있습니다. 하지만, 리눅스 서버가 재부팅되는 경우에는 Mariadb가 자동으로 실행되지 않습니다. 매번 서버를 재부팅할때마다 systemctl 명령을 통하여 MariaDB를 시작해 주어야 합니다.

서버가 실행될때 자동으로 MariaDB가 실행되도록 설정을 할 수 있습니다. enable 명령을 사용합니다.

```
hojin@hojin:~$ sudo systemctl enable mariadb
Synchronizing state of mariadb.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable mariadb
```

반대로 자동 실행을 해제할 경우에는 disable 명령을 사용합니다.

```
hojin@hojin:~$ sudo systemctl disable mariadb
Synchronizing state of mariadb.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install disable mariadb
Removed /etc/systemd/system/multi-user.target.wants/mariadb.service.
```



