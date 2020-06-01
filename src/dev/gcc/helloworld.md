---
layout: home
title: "gcc hello world 출력하기 - Learn Linux"
breadcrumb:
- dev
- gcc
- helloworld
---


# Hello World
---
gcc를 이용하여 `hello world`를 출력해 보도록 합니다.

<br>

## 환경설정
---
실습폴더를 하나 생성합니다.

```console
hojin@hojin1:~$ mkdir gcc
hojin@hojin1:~$ cd gcc
```

vscode를 실행합니다. 
wsl에서 code 명령을 입력하면, 자동으로 vscode용 wsl remote 프로그램이 설치됩니다.

```console
hojin@hojin1:~/gcc$ code
Installing VS Code Server for x64 (5763d909d5f12fe19f215cbfdd29a91c0fa9208a)
Downloading: 100%
Unpacking: 100%
Unpacked 2321 files and folders to /home/hojin/.vscode-server/bin/5763d909d5f12fe19f215cbfdd29a91c0fa9208a.
```

<br>

## 코드작성
---
hello.c 코드를 작성합니다.

```c
#include <stdio.h>

void main()
{
    printf("hello world\n");
}
```

작성한 코드를 컴파일 합니다.

```console
hojin@hojin1:~/gcc$ gcc hello.c
hojin@hojin1:~/gcc$ ls
a.out  hello.c
```

정상적으로 컴파일이 수행되면 `a.out` 파일이 생성됩니다. 파일을 실행합니다.

```console
hojin@hojin1:~/gcc$ ./a.out
hello world
```

`hello world`가 정상적으로 출력되었습니다.


