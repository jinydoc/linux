# virtual host
아파치 가상호스팅 설정을 할 수 있습니다.

httpd.conf 파일 추가
```
# Virtual hosts
Include conf/extra/httpd-vhosts.conf
```


## httpd-vhost.conf

```
NameVirtualHost *:80

<VirtualHost *:80>
    DocumentRoot "C:\shopping"
    ServerName shopping.com
    ServerAlias www.shopping.com      
</VirtualHost>
```

## 접속권한 설정
사용자 계정을 생성후에 웹사이트를 실행하게 되면 permission 오류가 발생을 합니다.

해당 계정이 웹서버에 접근을 할 수 있도록 권한을 추가적으로 부여를 해야 합니다.

```
# yum install mod_ruid2
```



## 참조
https://joont.tistory.com/46
http://blog.ivps.kr/72