---
layout: home
---

# 테스트 및 접속하기
---
설치 및 실행된 MariaDB에 접속해 보도록 합니다. 

<br>

## 실행하기
---
mariaDB의 데몬이 실행되어 있는 상태에서 `mysql`명령을 입력하면 클라이언트 프로그램이 실행됩니다.
mysql 실행스크립트 mysql은 /usr/bin/mysql 에 있습니다.


다음과 같이 입력합니다.
```
jiny@jiny:~$ mysql
ERROR 1698 (28000): Access denied for user 'jiny'@'localhost'
```

접속이 거부되었습니다.  아직 `jiny` 계정이 없기 때문에 접속이 거부된 것입니다.

sudo 명령을 같이 사용하여 루트권환으로 데이터베이스에 접속합니다. 

```
$sudo mysql
```

MariaDB의 접속 명령어는 mysql과 동일합니다. 초기에는 비밀번호가 없기 때문에 바로 접속이 됩니다.

```
jiny@jiny:~$ sudo mysql
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 44
Server version: 10.5.8-MariaDB-1:10.5.8+maria~focal mariadb.org binary distribution

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]>
```

MariaDB [(none)]> 이 출력되면 정상이다.

데이터베이스를 종료할 때에는 `exit`명령을 입력합니다.




