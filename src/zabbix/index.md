---
layout: home
---

# zabbix 설치

자빅스는 손쉬운 설치를 위해서 설치 스크립트 명령을 자동으로 생성해 줍니다.  
`https://www.zabbix.com/download` 로 접속을 합니다.

자신의 플렛폼 사항을 선택합니다.



![image-20210313162456263](D:\jinydev\linux\src\zabbix\img\image-20210313162456263.png)





## Ubuntu + mysql + apache 환경 설치



##### a. Install Zabbix repository

```
# wget https://repo.zabbix.com/zabbix/5.2/ubuntu/pool/main/z/zabbix-release/zabbix-release_5.2-1+ubuntu20.04_all.deb# dpkg -i zabbix-release_5.2-1+ubuntu20.04_all.deb# apt update
```

##### b. Install Zabbix server, frontend, agent

```
# apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-agent
```

##### c. Create initial database

](https://www.zabbix.com/documentation/5.2/manual/appendix/install/db_scripts)

Make sure you have database server up and running.

Run the following on your database host.

```
# mysql -uroot -ppasswordmysql> create database zabbix character set utf8 collate utf8_bin;mysql> create user zabbix@localhost identified by 'password';mysql> grant all privileges on zabbix.* to zabbix@localhost;mysql> quit;
```

On Zabbix server host import initial schema and data. You will be prompted to enter your newly created password.

```
# zcat /usr/share/doc/zabbix-server-mysql*/create.sql.gz | mysql -uzabbix -p zabbix
```

##### d. Configure the database for Zabbix server

Edit file /etc/zabbix/zabbix_server.conf

```
DBPassword=password
```

##### e. Start Zabbix server and agent processes

Start Zabbix server and agent processes and make it start at system boot.

```
# systemctl restart zabbix-server zabbix-agent apache2# systemctl enable zabbix-server zabbix-agent apache2
```

##### f. Configure Zabbix frontend

Connect to your newly installed Zabbix frontend: http://server_ip_or_name/zabbix
Follow steps described in Zabbix documentation: [Installing frontend](https://www.zabbix.com/documentation/5.2/manual/installation/install#installing_frontend)