# 양수종 contos



#### VirtualBox 설치하기

다운로드 

설치

센트os 설치



root 암호란?



#### 리눅스 명령어



date : 날짜

cal : 달력

cal 2021 년도 달력

```
$ cal 2021
```



지정한 달 출력

```
cal 1 2021
```





who : 접속한 사용자 출력

```
test@test:~$ who
test     tty1         2021-01-03 08:44
test     pts/0        2021-01-03 08:53 (10.0.2.2)

```



w : 현재 사용하고 있는 동작을 확인

```
test@test:~$ w
 12:59:43 up  4:16,  2 users,  load average: 0.00, 0.00, 0.00
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
test     tty1     -                08:44    3:13m 16.71s  0.84s -bash
test     pts/0    10.0.2.2         08:53    0.00s  0.07s  0.00s w

```





```
test@test:~$ users
test test
```



현재 아키텍쳐 를 확인

```
test@test:~$ arch
x86_64

```







지금 로그인한 사용자

```
test@test:~$ logname
test

```



현재 사용자의 id 정보를 출력

```
test@test:~$ id
uid=1000(test) gid=1000(test) groups=1000(test),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lxd)
```

일반적으로 사용자는 id가 1000번부터 부여됨



화면지울떼

^l



hostname

```
test@test:~$ hostname
test
```





