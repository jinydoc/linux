---
layout: home
---



# 셈플코드 작성

설치한 php를 통하여 간단한 동작 테스트 프로그램을 하나 작성해 보도록 합니다.



## 작성경로

php는 웹서버의 확장 모듈로 실행이 됩니다. 

아파치 웹서버의 경우 `/var/www/html`이 기본 경로 입니다.

<br>

## 코드 작성하기

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

<br>


## 브라우저 접속

브라우저를 싱행하여 localhost/test.php 경로를 접속해 봅니다.



![image-20210103125650466](D:\jinydev\linux\src\img\image-20210103125650466.png)



php가 잘 실행되는 것을 확인할 수 있습니다.

