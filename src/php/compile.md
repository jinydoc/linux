---
layout: home
---

# PHP 컴파일 설치
---
컴파일을 통하여 php를 설치 합니다.

<br>

## php 소스 다운로드 받기
---
최신의 php 소스는 php.net에서 다운로드 받을 수 있습니다.
소스를 다운로드 받습니다. 압축을 풀어 줍니다.

```
# wget https://www.php.net/distributions/php-8.0.0.tar.gz
# tar zxvf php-8.0.0.tar.gz
```

<br>

### 의존성 패키지 설치
---
의존되는 패키지는  컴파일로 같이 설치 할 수 없습니다. 필요한 패지키를 `apt` 명령어로 밀 설치를 해줍니다.

```
$ sudo apt install libxml2-dev libjpeg-dev libpng-dev
```

php를 설치하기 위해서는 apache2의 apxs 가 필요합니다. 이를 위해서 추가 패키지를 설치합니다.

```
sudo apt-get install apache2-dev
```

<br>

## 컴파일 실행하기
---
컴파일을 위한 소스가 모두 준비가 완료 되었다면, configure와 make 명령을 통하여 컴파일을 해보도록 합니다. 

```
$ cd php-8.0.0
$ ./configure \
--with-apxs2=/usr/local/apache2.4/bin/apxs \
--enable-mysqlnd \
--with-mysql-sock=mysqlnd \
--with-mysqli=mysqlnd \
--with-pdo-mysql=mysqlnd \
--with-imap-ssl \
--with-iconv \
--enable-gd \
--with-jpeg \
--with-libxml \
--with-openssl
$ make && make test && make install
```

