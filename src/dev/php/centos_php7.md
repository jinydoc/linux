---
layout: home
---

# php 7.2 centos 설치

CentOS는 yum을 이용하여 php 페키지를 설치할 수 있습니다.

## php 버전
centos의 경우 기본적으로 제공하는 php는 버전이 낮습니다. 5.x를 제공합니다.
하지만, PHP는 7.x로 올라가면서 많은 성능이 개선이 되었습니다.

최신의 PHP 버전을 설치하기 위해서는 추가 작업을 한후에 설치를 할 수 있습니다.

## yum 저장소 추가
최신의 php버전을 설치하기 위해서는 추가 yum 저장소를 등록해야 합니다.
외부 yum 저정소로 유명한 곳은 webtatic 과 remi가 있습니다.


새로운 외부 yum저장소를 추가합니다.


## 설치
CentOS는 기본적으로 오래된 PHP 5.4 버전을 지원합니다. 최신의 버전을 설치하기 위해서는 약간의 추가 작업이 필요로 합니다. 

먼저 yum 저장소를 추가합니다.
Remi CentOS 저장소를 추가합니다.

yum install http://rpms.remirepo.net/enterprise/remi-release-7.rpm

Disable Remi PHP 5.4 repository
By default, the repository for PHP 5.4 is enabled and hence, to install the latest version of PHP, you need to disable this repo. The repositories can be enabled or disabled using the yum-config-manager command. This command is provided with the yum-utils package.

yum install -y yum-utils
yum-config-manager --disable remi-php54
Enable Remi PHP 7.3 repository
To enable Remi PHP 7.3 repository, run the command below.

yum-config-manager --enable remi-php73

yum install php

설치를 확인합니다.

```
[root@jiny ~]# php -v
PHP 7.3.8 (cli) (built: Jul 30 2019 09:26:16) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.3.8, Copyright (c) 1998-2018 Zend Technologies

```

## 웹서버 재시작
php를 설치한 후에는 웹서버를 재시작 해주어야 합니다.

We must restart Apache to apply the changes:

 systemctl restart httpd.service



## 추가설치
yum list php-*
yum install php-<extension_name>


yum install php-mysql php-pdo









```
# rpm -Uvh http://rpms.remirepo.net/enterprise/remi-release-7.rpm
[root@jiny ~]# rpm -Uvh http://rpms.remirepo.net/enterprise/remi-release-7.rpm
Retrieving http://rpms.remirepo.net/enterprise/remi-release-7.rpm
warning: /var/tmp/rpm-tmp.raA66z: Header V4 DSA/SHA1 Signature, key ID 00f97f56: NOKEY
error: Failed dependencies:
        epel-release = 7 is needed by remi-release-7.6-2.el7.remi.noarch

```

Install yum-utils as we need the yum-config-manager utility.

```
yum install yum-utils
```

그리고 yum을 최신으로 업데이트 합니다.

```
yum update
```

Now you have to chose which PHP version you want to use on the server. If you like to use PHP 5.4, then proceed to chapter 4.1. To install PHP 7.0, follow the commands in chapter 4.2, for PHP 7.1 chapter 4.3, for PHP 7.4 use chapter 4.4 and for PHP 7.3 follow chapter 4.5 instead. Follow just one of the 4.x chapters and not all of them as you can only use one PHP version at a time with Apache mod_php.


### php 5.4
권장하지 않습니다. 기본적으로 설치되어 있는 오래된 버전입니다. 

```
# yum install php
```
명령을 입력하면 설치할 수 있습니다.


### 7.0
We can install PHP 7.0 and the Apache PHP 7.0 module as follows:

```
yum-config-manager --enable remi-php70
yum install php php-opcache
```

### 7.1
If you want to use PHP 7.1 instead, use:

```
yum-config-manager --enable remi-php71
yum install php php-opcache
```

### 7.3
If you want to use PHP 7.3 instead, use:

```
# yum-config-manager --enable remi-php73
# yum install php php-opcache
```




## 확인 및 테스트
웹서버의 기본 문서 위치는 /var/www/html 입니다. 이 위치에 테스트를 위한 php 파일을 만들어 보도록 합니다.

```
<?php
phpinfo();
```



## 참조 블로그 및 url
* https://blog.asamaru.net/2018/02/14/install-php-7-2-on-centos-with-remi-rpm-repository/
* https://www.howtoforge.com/tutorial/centos-lamp-server-apache-mysql-php/#-install-php--5
* https://kifarunix.com/installing-php-7-3-3-on-centos-7-6/
