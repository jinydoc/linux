---
layout: home
---

# PostgreSql 설치하기



#### 준비하기

페키지 목록을 최신 상태로 유지합니다.

```
$ sudo apt update
```



설치하기

```
$ sudo apt-get install postgresql postgresql-contrib
```



postgresql 설치시 기본적으로 postgres 계정이 생성됩니다.

postgres 계정은 PostgreSql을 관리하기 위한 계정 입니다.

postgres 계정으로 변경합니다.

```
sudo -i -u postgres
```



## DB 접속하기

psql 명령을 입력하여 DB에 접속해 봅니다.



```
postgres@test:~$ psql
psql (12.5 (Ubuntu 12.5-0ubuntu0.20.04.1))
Type "help" for help.

postgres=#
```

현재 설치된 버젼은 12.5 입니다.



또는 sudo 계정으로 postgreSql에 바로 접속을 할때에는 다음과 같이 입력합니다.

```
sudo -u postgres pgsql
```

test 사용자 계정에서 다음과 같이 postgreSql로 바로 진입하는 것을 볼 수 있다.

```
test@test:~$ sudo -u postgres psql
psql (12.5 (Ubuntu 12.5-0ubuntu0.20.04.1))
Type "help" for help.

```



#### 종료하기

postgreSql에서 종료하고 나갈때는 `\q`를 입력합니다.

```
postgres=# \q
postgres@test:~$
```



## 사용자 추가

새로운 사용자를 추가할때

```
test@test:~$ sudo -i -u postgres
postgres@test:~$ createuser --interactive
Enter name of role to add: jiny
Shall the new role be a superuser? (y/n) y
```

새로운 사용자를 추가할 때에는 `createuser` 명령을 사용합니다. 이때 옵션 `--interactive`을 같이 입력합니다.

새로운 사용자 명을 입력 받고, 이 유저가 superuser 인지를 물어 봅니다.



createuser 명령에 대한 자세한 사용법은 

```
man createuser
```

 를 입력합니다.





#### DB 생성하기

새로운 db를 생성할때는 createdb 명령을 사용합니다.

```
postgres@test:~$ createdb jinyphp
```



#### 리눅스 계정

postgreSql은 데이터베이스와 동일한 리눅스 계정이 필요합니다.

```
test@test:~$ sudo adduser jinyphp
Adding user `jinyphp' ...
Adding new group `jinyphp' (1001) ...
Adding new user `jinyphp' (1001) with group `jinyphp' ...
Creating home directory `/home/jinyphp' ...
Copying files from `/etc/skel' ...

```



> 즉, PostgreSQl 데이터베이스 명과 postgres 사용자명과 리눅스 계정이 동일하게 필요합니다.



이제 만들어진 계정으로 데이터베이스를 접속해 봅니다.

```

test@test:~$ sudo -u jinyphp psql -d jinyphp
psql (12.5 (Ubuntu 12.5-0ubuntu0.20.04.1))
Type "help" for help.

jinyphp=#

```



DB 접속정보를 확인합니다.

```
jinyphp=# \conninfo
You are connected to database "jinyphp" as user "jinyphp" via socket in "/var/run/postgresql" at port "5432".
```



테이블 확인 `\d`

타입이 table인 것만 확인하려면 \dt 명령으로 확인할 수 있다.





쿼리를 통한 사용자 계정 추가

```
postgres=# CREATE USER 아이디 WITH PASSWORD '비밀번호';
```



데이터베이스 생성

```
postgres=# CREATE DATABASE 데이터베이스명 OWNER 아이디;
```



스키마 

```
postgres=# CREATE SCHEMA 스키마 AUTHORIZATION 아이디;

-- public 스키마가 아닌 별도의 스키마를 생성해서 사용하려면 search_path 를 잡아주는 것이 편하다.
-- search_path는 탐색할 스키마의 순서를 지정해주는 변수다.
-- show search_path;
postgres=# alter USER bcadmin set search_path = 'bcpaltform';
```

