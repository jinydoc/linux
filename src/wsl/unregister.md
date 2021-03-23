---
layout: home
---

# 설치된 wsl 삭제하기
---
윈도우에 설치된 wsl을 console 명령을 통하여 삭제할 수 있습니다.   



<br>



## 1. 설치목록 확인하기

먼저 windows 시스템에 설치되어 있는 wsl을 확인합니다. CMD 콘솔창에서 `wsl -l` 명령을 입력합니다. 

```
C:\> wsl -l
Linux용 Windows 하위 시스템 배포:
Ubuntu-20.04(기본값)
```

window 컴퓨터에는 복수개의 wsl 환경을 구축할 수 있습니다. 현재 시스템에 `Ubuntu-20.04` 한개가 설치되어 있는 것을 확인할 수 있습니다.



<br>



## 2.삭제명령 실행

설치된 wsl을 삭제하는 방법은 `--unregister` 옵션을 사용하는 것입니다.  

다음과 같이 설치된 Ubuntu-20.04를 삭제해 보도록 합니다.  

```
C:\> wsl --unregister Ubuntu-20.04
등록 취소 중...
```



<br>



## 3.확인

windows 컴퓨터에서 설치한 wsl이 잘 삭제가 되었는지 확인해 보도록 합니다.  

`-l`옵션을 이용하여 다시 목록을 확인합니다.

```
C:\> wsl -l
Linux용 Windows 하위 시스템에 배포가 설치되어 있지 않습니다.
아래의 Microsoft Store에서 배포를 설치할 수 있습니다.
https://aka.ms/wslstore
```

삭제후 아무런 wsl이 설치가 되어 있지 않다고 표시가 됩니다. 새로운 wsl을 설치하려면 windows 의 store에서 검색하여 설치를 하실 수 있습니다.  

