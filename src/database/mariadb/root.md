---
layout: home
---

# root 설정하기
---
앞에서 우리는 비밀번호를 지정하지 않아도 MariaDB에 접속이 가능하였습니다. 

Mysql 명령어만 실행하면, 현재 운영체제 사용자와 같은 이름인 root로 비밀번호 없이 접속이 되는 것이다.

<br>

## root 비밀번호
---
비밀번호 없이 데이터베이스 접속하는 것은 보안측면에서 좋지 않습니다. 
보안을 위해서 root 비밀번호를 설정합니다. 다음과 같이 명령을 입력합니다.

기본적으로 패키지만 설치하는 경우 root 암호가 없다. 별도로 지정을 해주어야 한다.

DB를 설치할 때 root 사용자가 하나 추가 된다.



#### mysqladmin

mysqladmin 유틸리티를 통한 비밀번호를 변경합니다.

```
$ sudo mysqladmin -u root password '패스워드'
```



이렇게 설정한 패스워드는 mysql 접속시 다음과 같이 입력합니다. 

```
Mysql -u 사용자명 -p
```

<br>

## mysql root 비빌번호 분실
---
root 비밀번호를 분실한 경우 다음과 같이 재설정한다.

####  step1. mysqld 중지
먼저 마리아DB 서버데몬을 중지합니다.

```
$ sudo systemctl stop mariadb
```

마리아DB를 `안전 모드`로 실행을 합니다. 
다음과 같이 mysql_safe 스크립트를 통하여 실행이 가능합니다.

```
$ sudo /usr/bin/mysqld_safe --skip-grant &
```

> `&` 표시를 같이하게 되면, `백그라운드` 모드로 마리아DB가 실행이 됩니다.



#### step2. root계정 비밀번호 변경

백그라운드로 실행되는 마리아DB에 접속을 합니다. 이때 패스워드는 지정하지 않아도 됩니다.

```
$ sudo mysql -u root
```

sql 쿼리를 이용하여 root 사용자의 패스워드를 변경합니다.

```
MariaDB [mysql]> update user set password=password('변경할 비밀번호') where user='root';
MariaDB [mysql]> flush privileges;
MariaDB [mysql]> exit;
```
 

#### step3. 접속 확인
변경한 패스워드를 이용하여 접속을 테스트 해봅니다.

```
mysql -uroot -p
Enter password:
MariaDB [(none)]> 
```
 

#### step4. 서비스 재시작
root 비밀번호가 잘 변경이 되었다면, 마리아DB를 재실행 합니다.

```
$ sudo systemctl stop mariadb
$ sudo systemctl start mariadb
```


