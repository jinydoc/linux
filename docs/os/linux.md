# 리눅스

리눅스 서버로 가장 많이 하는 것 => 웹서비스



브라우저에서 보여지는 웹페이지 html을 가지고 위한 웹서버

웹서버 => 웹페이지를 보여주기 위한 서비스



서버용 운영체제 => 리눅스



웹서비스

메일

채팅

ftp

dhcp

외 다양한 서비스



네트워크 운영체제 시스템 NOS





리눅스 공부



1.일반사용자: 파일 관리, 내용을 수정할 수 있는 vi

쉘 동작 및 처리등 공부





2.관리자 : root란, 설치, 프로세스, 패키지, 사용자 관리 등에 대해서 공부

시스템에 대한 관리, 계정을 통한 일반 사용자 관리



3. 서비스 관리

웹,메일, dns, ftp 등 관리



4. 보안

로그관리, 포트 관리



5. 프로그래밍

   gcc, g++, make, shell 프로그래밍 등 공부





#### 리눅스탄생

리누스토발즈 

unix 1969년도 탄생, C언어 1971년도 탄생, 



#### 오픈소스 와 라이센스



#### 배포판

RadHat 계열, Ubuntu 계열



redhat -> fedora -> centos



데비안 -> 우분투





#### 일반 사용자

`$` 일반사용자

`#`  관리자



#### 경로(path)

`.` : 현재 디렉토리 표시

`..`: 부모 디렉토리를 표시

`/` : 최상의 루트 디렉토리 

`~` : 사용자 홈 디렉토리



```
test@test:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin

```

경로 안에 있는 파일들은 실행이 가능하다.



경로가 설정되어 있지 않는 파일은 직접 모든 경로를 다 입력해 주어야 한다.



#### 파일 다루기

* 생성 : mkdir, vi, cat, touch
* 복사 : cp
* 삭제 : rm, rmdir
* 이동 : mv
* 변경 : rename



파일 vs 디렉터리(폴더)



리눅스는 모든것을 파일로 취급한다.

리눅스는 특이하게도 장비, 디렉터리등 모두를 파일로 취급한다.



용어설명

* -r recursive : 재귀적으로 하위 디렉토리를 포함하여 작업

* -i interactive : 대화형 모드, 물어보는 역할

* -f force : 강제로 진행



#### 리눅스 도움말

명령어의 구조

[option]

] 생략가능

... 중복허용



```

test@test:~$ man ls
NAME
       ls - list directory contents

SYNOPSIS
       ls [OPTION]... [FILE]...
```



```
SYNOPSIS
       cp [OPTION]... [-T] SOURCE DEST
       cp [OPTION]... SOURCE... DIRECTORY
       cp [OPTION]... -t DIRECTORY SOURCE...

```

대괄호가 없으면, 생략이 불가능 하기 때문에 반드시 필요함



명령어 --help

도움말 빠져 나오기 `q`



info 명령어

man 명령어



#### 파일 분류하기

파일은 크게 `일반 파일`과 `특수파일`로 분류한다.



일반파일이란 text, 바이너리 파일을 말합니다.

* 텍스트
* 바이너리



특수파일이란, 디렉토리 와 장치파일들이 있습니다.

* 디렉터리
* 장치파일
  * block : 저장장치와 같은 
  * char : 키보드와 같은



링크파일

* 하드링크 : 래퍼런스 변수와 유사
* 소프트링크(심볼링크) : 포인터 변수와 유사, 윈도우 바로가기와 유사





