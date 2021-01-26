# MariaDB 설치하기



## 01.설치

Mariadb를 설채해 보도록 합니다.



### 설치확인

먼저 mariadb가 설치되어 있는지 확인해 보도록 합니다.

```
$dpkg -l | grep mariadb
```

아무런 메시지가 없다면, 설치된 mariadb 패키지가 없다는 의미 입니다.



### 사전 준비작업

리눅스 패포판은 기본적으로 최신 버젼의 패키지를 제공하지 않습니다. 최신의 mariadb를 설치하기 위해서는 목록을 갱신해 주어야 합니다.

저장소의 목록은 https://mariadb.org/download/#mariadb-repositories 에서 확인을 할 수 있습니다.



![image-20210101152711026](D:\onedrive\강의준비\linux\img\image-20210101152711026.png)



Linux 패보판 운영체제와 설치하고자 하는 MaraiaDB 버젼을 선택합니다. 그럼 입력해야 하는 목록을 자동적으로 생성해 줍니다. 이를 실행합니다.



```bash
$ sudo apt-get install software-properties-common dirmngr apt-transport-https
$ sudo apt-key adv --fetch-keys 'https://mariadb.org/mariadb_release_signing_key.asc'
sudo add-apt-repository 'deb [arch=amd64,arm64,ppc64el] https://mirror.yongbok.net/mariadb/repo/10.5/ubuntu focal main'
```

새로운 패키지 저장소 목록을 추가했다면, 목록을 갱신합니다.



```bash
$ sudo apt update
```





### 패키지 설치

최신 버젼의 Mariadb를 설치할 수 있도록 목록을 갱신하였습니다. 다음과 같이 명령을 입력하여 mariadb를 설치합니다.

```
$ sudo apt install mariadb-server -y
```



설치가 완료 되었면 자동으로 MariaDB가 실행됩니다. 다음과 같이 프로세스를 확인해 봅니다.

```
hojin@hojin:~$ ps -ef | grep mysql
mysql       4815       1  0 15:32 ?        00:00:00 /usr/sbin/mariadbd
hojin       5812    2266  0 15:34 pts/0    00:00:00 grep --color=auto mysql
```



버젼확인하기

```
hojin@hojin:~$ sudo mariadb --version
mariadb  Ver 15.1 Distrib 10.3.25-MariaDB, for debian-linux-gnu (x86_64) using readline 5.2
```





### 02.MaraiDB 접속하기

설치 및 실행된 MariaDB에 접속해 보도록 합니다. 



\#mysql 을 입력합니다.  실행스크립트 mysql은 /usr/bin/mysql 이다.



다음과 같이 입력합니다.

```
hojin@hojin:~$ mysql
ERROR 1698 (28000): Access denied for user 'hojin'@'localhost'
```

접속이 거부되었습니다.  아직 `hojin` 계정이 없기 때문에 접속이 거부된 것입니다.



sudo 명령을 같이 사용하여 루트권환으로 데이터베이스에 접속합니다. 

```
$sudo mysql
```

MariaDB의 접속 명령어는 mysql과 동일합니다. 초기에는 비밀번호가 없기 때문에 바로 접속이 됩니다.

```
hojin@hojin:~$ sudo mysql
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 44
Server version: 10.5.8-MariaDB-1:10.5.8+maria~focal mariadb.org binary distribution

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]>
```

MariaDB [(none)]> 이 출력되면 정상이다.

데이터베이스를 종료할 때에는 `exit`명령을 입력합니다.







## 시작/정지/상태/활성화

서버를 실행, 정지, 재시동, 상태를 확인할 수 있습니다.

Apt 명령어로 설치를 할 경우

/etc/system/system에 서비스이름.service 또는 서비스이름.socket으로 등록된다.

 

시작 systemctl start 서비스 이름

상시 기동설정 systemctl enable 서비스이름



### 상태확인

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



### 서버 정지하기

```
$ sudo systemctl stop mariadb
```



### 서버 실행하기

```
$ sudo systemctl start mariadb
```



또는

```
$ sudo service mysql start
```





### 항상 실행하기

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



## 03.환경 설정하기

MariaDB를 사용하기 위한 간단한 설정을 합니다.



### root 비밀번호 설정하기

앞에서 우리는 비밀번호를 지정하지 않아도 MariaDB에 접속이 가능하였습니다. Mysql 명령어만 실행하면, 현재 운영체제 사용자와 같은 이름인 root로 비밀번호 없이 접속이 되는 것이다.



비밀번호 없이 데이터베이슬 접속하는 것은 보안측면에서 좋지 않습니다. 보안을 위해서 root 비밀번호를 설정합니다. 다음과 같이 명령을 입력합니다.

기본적으로 패키지만 설치하는 경우 root 암호가 없다. 별도로 지정을 해주어야 한다.

DB를 설치할 때 root 사용자가 하나 추가 된다.

mysqladmin 유틸리티를 통한 비밀번호 변경

```
$ sudo mysqladmin -u root password ‘패스워드’
```



원칙적으로 DB에 접속을 하기위해서

Mysql -u 사용자명 -p

형태로 입력을 해야 한다.



### 접속허용



#### 외부에서 접속하기

DB는 기본적으로 외부로부터 접속을 되지 않도록 설정되어 있다.

/etc/mysql/mariadb.conf.d/50-server.conf 파일을 수정합니다. bind-address 부분을 주석 처리합니다.

```
$ sudo vi /etc/mysql/mariadb.conf.d/50-server.conf
```



```
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
#bind-address            = 127.0.0.1
```



#### 외부 접속을 위한 root 사용자 계정 변경

두번째, DB의 사용자는 권한을 사용자명@호스트/IP주소 형태로 관리 합니다.

기본값은 root@localhost 로 되어 있어 localhost 외의 컴퓨터에서 접속이 불가능 하다.



```
create user '아이디'@'%' identified by '비밀번호';
grant all privileges on *.* to '아이디'@'%';
```



기본적으로 MariaDB의 root 계정은 localhost의 터미널 계정에서만 접속이 가능합니다. 

만일 다른 외부툴을 이용하여 접속을 하기 위해서는 권환을 추가해 주어야 합니다.

이러한 접속 가능한 컴퓨터를 지정하는 사용자 계정은 동적으로 IP를 할당받는 환경에서는 접속이 어려울수 있다. 매번 컴퓨터를 켤때마다 IP주소가 변경되기 때문이다.



```
MariaDB [(none)]> create user 'root'@'%' identified by '패스워드';
Query OK, 0 rows affected (0.005 sec)

MariaDB [(none)]> grant all privileges on *.* to 'root'@'%';
Query OK, 0 rows affected (0.012 sec)

MariaDB [(none)]> flush privileges;
Query OK, 0 rows affected (0.001 sec)
```



127.0.0.1

:::1

Localhost

Server

현재 자신의 컴퓨터를 가리키는 동일한 의미



또는 특정 IP 영역으로 선택할때는 다음과 같이 할 수도 있습니다.

```
Grant all privileges on *.* to 사용자명@’192.168.1.%’ IDENTIFIED BY ‘1234’;
```

%는 해당 아이피를 모드 허용하는 xxx값과 같다.

Grant 는 사용자를 생성해 주는 SQL문 이다.

Grant 사용권환 ON 데이터베이스명.테이블 to 사용자명@’호스트’ IDENTIFIED BY ‘비밀번호’;

 

사용권한을 모두 부여할 경우에는 ALL PRIVILEGES 로 입력하면 됩니다.

 

모든 스키마와 데이블을 지정할 경우 *.* 로 입력합니다.



#### 서버를 재시작 합니다.



그리고 서비스를 재시작 합니다. 이제 다른 컴퓨터에서도 DB에 접속이 가능하다.

```
$ sudo systemctl restart mariadb
```



#### 방화벽 허용

우분투의 기본적인 방화벽은 UFW입니다. 

UWF는 iptables를 좀 더 쉽게 설정할 수 있도록 한 것입니다.

UWF는  간단한 방화벽 구성에는 문제가 없지만 수준 높은 방화벽 구성을 하기 위해서는 iptables 룰을 직접 사용해야 합니다.



```
# ufw allow 3306
```



#### Virtual Box 포트 포워드 허용

VirtualBox, VmWare등의 가상 환경 솔루션을 통하여 외부에서 DB에 접속을 하기 위해서는 포트 설정이 필요로 합니다. 

[장치] >[네트워크]>[네트워크 설정] 을 선택합니다.



![image-20210101155438912](D:\onedrive\강의준비\linux\img\image-20210101155438912.png)



고급을 선택하여 설정창을 확대합니다. `포트 포워딩`을 선택합니다.

![image-20210101155546639](D:\onedrive\강의준비\linux\img\image-20210101155546639.png)

3106 포트 포워딩을 추가합니다. MariaDB는 Mysql과 동일하게 3106 포트 번호를 이용합니다.

![image-20210101155715995](D:\onedrive\강의준비\linux\img\image-20210101155715995.png)





#### 원격으로 접속하기

다른 서버에 접속을 할 경우에는 mysql -h 서버주소 -u 사용자명 -p 를 입력합니다.

윈도우 컴퓨터에서 VirtualBox로 Mariadb를 접속해 봅니다.

```
C:\Bitnami\wampstack-8.0.0-0\mysql\bin>mysql -u root -p
Enter password: ******
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 14
Server version: 5.5.5-10.3.25-MariaDB-0ubuntu0.20.04.1 Ubuntu 20.04

Copyright (c) 2000, 2020, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

성공적으로 접속이 되는 것을 확인할 수 있습니다.



















## Tip. mysql root 비빌번호 분실

root 비밀번호를 분실한 경우 다음과 같이 재설정한다.



##  mysqld 중지

```
$ sudo systemctl stop mariadb
```



안전 모드로 실행을 합니다.

```
$ sudo /usr/bin/mysqld_safe --skip-grant &
```



```
$ sudo mysql -u root
```

### 3. 안전모드로 접속해서 root계정 비밀번호 변경

mysql -uroot mysql

MariaDB **[**mysql**]>** update user set password=password**(**'변경할 비밀번호'**)** where user='root';

MariaDB **[**mysql**]>** flush privileges;

MariaDB **[**mysql**]>** exit;

 

### 4. 접속 확인

mysql -uroot -p

Enter password:

MariaDB **[(**none**)]>** 

 

### 5. 서비스 재시작

systemctl stop mariadb

systemctl start mariadb



출처: https://baejangho.com/entry/MariaDB-비밀번호-분실한-경우-새-비밀번호-생성 [호짱의 개발 블로그]