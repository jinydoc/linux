---
layout: home
---

# 아파치 설치

## centos
centos linux에서는 yum을 통하여 아파치를 설치할 수 있습니다.

```
# yum install httpd
```

또는 
```
# yum -y install httpd
```

```
================================================================================
 Package           Arch         Version                     Repository     Size
================================================================================
Installing:
 httpd             x86_64       2.4.6-89.el7.centos.1       updates       2.7 M
Installing for dependencies:
 httpd-tools       x86_64       2.4.6-89.el7.centos.1       updates        91 k
 mailcap           noarch       2.1.41-2.el7                base           31 k

Transaction Summary
================================================================================
Install  1 Package (+2 Dependent packages)

Total download size: 2.8 M
Installed size: 9.6 M
Is this ok [y/d/N]:
```


y를 확인합니다.


## 아파치 실행하기
리눅스 서버에 아파치가 설치가 되었다면 서버를 실행합니다.


```
[root@jiny ~]# systemctl start httpd
[root@jiny ~]# 
```

서버를 실행 명령을 입력을 하면, 별다른 메시지가 출력되지 않습니다.

상태를 통하여 서버 실행 여부를 확인합니다.

```
[root@jiny ~]# systemctl status httpd
● httpd.service - The Apache HTTP Server
   Loaded: loaded (/usr/lib/systemd/system/httpd.service; disabled; vendor preset: disabled)
   Active: active (running) since Sun 2019-08-11 18:48:36 KST; 1min 7s ago
     Docs: man:httpd(8)
           man:apachectl(8)
 Main PID: 3197 (httpd)
   Status: "Total requests: 0; Current requests/sec: 0; Current traffic:   0 B/sec"
   CGroup: /system.slice/httpd.service
           ├─3197 /usr/sbin/httpd -DFOREGROUND
           ├─3198 /usr/sbin/httpd -DFOREGROUND
           ├─3199 /usr/sbin/httpd -DFOREGROUND
           ├─3200 /usr/sbin/httpd -DFOREGROUND
           ├─3201 /usr/sbin/httpd -DFOREGROUND
           └─3202 /usr/sbin/httpd -DFOREGROUND

Aug 11 18:48:36 jiny systemd[1]: Starting The Apache HTTP Server...
Aug 11 18:48:36 jiny httpd[3197]: AH00558: httpd: Could not reliably determine th...age
Aug 11 18:48:36 jiny systemd[1]: Started The Apache HTTP Server.
Hint: Some lines were ellipsized, use -l to show in full.

```
서버가 실행되고 있는 것을 확을 할 수 있습니다.

### 자동실행추가
만일 서버가 재시작을 할경우에, 아파치 웹서버는 자동으로 실행이 되지 않습니다. 수동으로 실행 명령을 다시 해주어야 합니다.

```

[root@jiny ~]# systemctl enable httpd.service
Created symlink from /etc/systemd/system/multi-user.target.wants/httpd.service to /usr/lib/systemd/system/httpd.service.

```

자동실행을 등록하시면 재부팅후에서 아파치 웹서버가 자동실행 됩니다.

