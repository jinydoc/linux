---
layout: home
breadcrumb:
- setup
---

# WSL2 활성화
---

그동안 windows 운영체제는 리눅스 환경을 같이 제공하기 위한 다양한 노력이 있었습니다. 그 결과로 wsl은 버젼1과 버젼2로 나누어지게 됩니다.



<br>



## 버젼1

windows store에서 기본적인 리눅스 배포본을 설치하게 되면, `버젼1`의 상태로 깔리게 됩니다.  

버젼1로도 충분히 리눅스 환경을 사용할 수 있지만, 몇몇의 특수한 리눅스 환경을 사용하기 위해서는 `버젼2`로 업그레이드가 필요로 합니다.



<br>



## 버젼2

windows wsl`버젼1`을 `버젼2`로 변경을 하기 위해서는 약간의 추가 작업이 필요로 합니다.


* step1: 최신 윈도우로 버전을 유지해 주세요.
* step2: 설정->insider program에 참여를 합니다.
* step3: windows subsystem for linux 를 활성화 합니다.



#### 현재 wsl 버젼 확인하기

wsl `-v`옵션을 이요하여 현재의 배포본이 어떠한 상태인지를 확인합니다.

```console
C:\Users\infoh>wsl -l -v
  NAME            STATE           VERSION
* Ubuntu-20.04    Running         1
```
한개의 리눅스 배포본이 설치되어 있고, 버젼은 1이라는 목록을 출려합니다.  



#### 버젼 올리기

설치된 Ubuntu-20.04 를 `버젼2`로 변경을 합니다. 이때 사용하는 옵션은 `--set-version`입니다.  사용방법은 다음과 같습니다.  

```
wsl --set-version 우분트 2
```

그럼 변경을 해보도록 합니다.

```
C:\Users\infoh>wsl --set-version Ubuntu-20.04 2
변환이 진행 중입니다. 몇 분 정도 걸릴 수 있습니다...
WSL 2와의 주요 차이점에 대한 자세한 내용은 https://aka.ms/wsl2를 참조하세요
변환이 완료되었습니다.
```
wsl1을 wsl2로 버젼을 변경합니다. 변경을 하는데는 컴퓨터 사양에 따라서 다소 시간이 걸립니다.  

변환이 완료된 후에 다시 한번 목록을 확인합니다.  

```
C:\Users\infoh>wsl -l -v
  NAME            STATE           VERSION
* Ubuntu-20.04    Stopped         2
```

wsl2 버젼으로 잘 변경이 된 것을 확인할 수 있습니다.



