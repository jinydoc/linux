---
layout: home
breadcrumb:
- setup
---

# WSL2 활성화
---
* step1: 최신 윈도우로 버전을 유지해 주세요.
* step2: 설정->insider program에 참여를 합니다.
* step3: windows subsystem for linux 를 활성화 합니다.

```console
PS C:\Windows\system32> wsl -l
Linux 배포용 Windows 하위 시스템:
Ubuntu-20.04(기본값)
```


```
wsl --set-version 우분트 2
```

```
wsl -l -v
```


## putty SSH 접속
[putty](https://www.putty.org/)를 다운로드 받습니다.



## 기본설정
---

시간대 설정
서버의 설정이 한국/서울로 안되어 있는 경우가 있습니다.

```
```



## 로케일(locale) 변경


## 관리자(sudo)

