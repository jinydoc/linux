# PHP 설치



## 01.설치하기

패키지를 이용하여 간단하게 설치를 합니다.

```
# sudo apt install php -y
```

ubuntu 20.04의 경우 php 7.4가 기본적으로 설치됩니다. 그이상의 버젼은 별도의 패키지 저장소를 등록하거나 컴파일 하여 설치를 해야 합니다.



#### 실행

php는 별도의 데몬이 실행되지 않습니다. 터미널 콘솔 또는 웹서버스 확장모듈 형태로 동작을 합니다.

터미널에서 `php -v`명령을 통하여 설치 버젼을 확인해 봅니다. 

```
test@test:~$ php -v
PHP 7.4.3 (cli) (built: Oct  6 2020 15:47:56) ( NTS )
Copyright (c) The PHP Group
Zend Engine v3.4.0, Copyright (c) Zend Technologies
    with Zend OPcache v7.4.3, Copyright (c), by Zend Technologies
```



## 02. 브라우저 확인

php는 웹서버의 확장 모듈로 실행이 됩니다.

아파치 웹문서의 경로에 실습 파일을 하나 작성해 봅니다.



```
$ sudo vi /var/www/html/test.php
```

vi 편집기를 이용하여 다음과 같이 입력을 해봅니다.  `esc+i`로 편집모드로 변경합니다.

```php
<?php
phpinfo();
```

`esc+:wq`로 저장후 종료 합니다.



#### 브라우저 접속

브라우저를 싱행하여 localhost/test.php 경로를 접속해 봅니다.



![image-20210103125650466](D:\onedrive\강의준비\linux\img\image-20210103125650466.png)



php가 잘 실행되는 것을 확인할 수 있습니다.

