---
layout: home
---

## 아파치 설치
---

```
sudo apt install apache2
```

아파치 index의 기본 경로는 /var/www/html

## PHP 설치
---

```
sudo apt install php
```

### xdebug  설치

```console
sudo apt install php-pear php-dev
pecl install xdebug
```

php.ini에 익스텐션을 해주면 된다.

cd /etc/php/7.2/apache2
sudo vim php.ini

에디터가 열린 상태에서 shift+g 를 누르면 맨 하단으로 내려가고

i를 누르면 insert모드로 변경

맨 하단에

```
[XDEBUG]
zend_extension=/usr/lib/php/20170718/xdebug.so //추가 후
```
esc -> :wq 입력

## 아파치 웹서버 실행

sudo service apache2 start