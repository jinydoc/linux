---
layout: home
---

# 아파치 웹서버

## 설치
---
apt 패키지 메니저를 통하여 apache2 를 설치합니다.

```console
sudo apt -y install apache2
```

<br>

## 설치 확인
---

```console
hojin@DESKTOP-11LMH3B:~$ dpkg -l | grep apache
ii  apache2                        2.4.41-4ubuntu3                   amd64        Apache HTTP Server
ii  apache2-bin                    2.4.41-4ubuntu3                   amd64        Apache HTTP Server (modules and other binary files)
ii  apache2-data                   2.4.41-4ubuntu3                   all          Apache HTTP Server (common files)
ii  apache2-utils                  2.4.41-4ubuntu3                   amd64        Apache HTTP Server (utility programs for web servers)
hojin@DESKTOP-11LMH3B:~$
```

<br>

## 서버실행
---
설치된 아파치2를 실행합니다.

```console
hojin@DESKTOP-11LMH3B:~$ sudo service apache2 start
 * Starting Apache httpd web server apache2                                                                             [Thu May 21 16:53:45.353412 2020] [core:warn] [pid 13856] (92)Protocol not available: AH00076: Failed to enable APR_TCP_DEFER_ACCEPT
sleep: cannot read realtime clock: Invalid argument
sleep: cannot read realtime clock: Invalid argument
sleep: cannot read realtime clock: Invalid argument
sleep: cannot read realtime clock: Invalid argument
 *
```

<br>

## 브라우저 접속
---
브라우저에서 `localhost`를 선택합니다.


