---
layout: home
---

# 설치된 wsl 삭제하기
---
윈도우에 설치된 wsl을 console 명령을 통하여 삭제할 수 있습니다. 
먼저 시스템에 설치되어 있는 wsl 목록을 확인합니다. 

```
C:\> wsl -l
Linux용 Windows 하위 시스템 배포:
Ubuntu-20.04(기본값)
```

현재 시스템에 `Ubuntu-20.04` 한개가 설치되어 있습니다.  
wsl 명령의 `--unregister` 옵션을 통하여 설치된 우분트를 삭제합니다.

```
C:\> wsl --unregister Ubuntu-20.04
등록 취소 중...
```

삭제후 다시 목록을 확인해 보도록 합니다.

```
C:\> wsl -l
Linux용 Windows 하위 시스템에 배포가 설치되어 있지 않습니다.
아래의 Microsoft Store에서 배포를 설치할 수 있습니다.
https://aka.ms/wslstore
```
