---
layout: home
title: "cal - linux 명령어"
keyword: "cal, linux"
description: "달력을 출력합니다."
breadcrumb:
- setup
---

# cal
---
달력을 출력합니다.

```console
hojin@DESKTOP-11LMH3B:~$ cal
      May 2020
Su Mo Tu We Th Fr Sa
                1  2
 3  4  5  6  7  8  9
10 11 12 13 14 15 16
17 18 19 20 21 22 23
24 25 26 27 28 29 30
31
```

## 한글 달력
---
기본 설정값은 영문 달력입니다. 로케일을 변경하여 한글 달력을 출력할 수 있습니다.

`locale` 명령을 통하여 설정을 확인합니다.
```console
hojin@DESKTOP-11LMH3B:~$ locale
LANG=C.UTF-8
LANGUAGE=
LC_CTYPE="C.UTF-8"
LC_NUMERIC="C.UTF-8"
LC_TIME="C.UTF-8"
LC_COLLATE="C.UTF-8"
LC_MONETARY="C.UTF-8"
LC_MESSAGES="C.UTF-8"
LC_PAPER="C.UTF-8"
LC_NAME="C.UTF-8"
LC_ADDRESS="C.UTF-8"
LC_TELEPHONE="C.UTF-8"
LC_MEASUREMENT="C.UTF-8"
LC_IDENTIFICATION="C.UTF-8"
LC_ALL=
```

`LANG=C.UTF-8` 로 설치가 되어 있습니다.



