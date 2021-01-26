



### 확장 설치 copy and past

#### 의존 패키지 설치

우부투 운영체제의 경우 의존 패키지를 설치합니다.

```
$ sudo apt-get install -y dkms build-essential linux-headers-generic linux-headers-$(uname -r)
```



#### CD롬 삽입

```
$ sudo mount /dev/cdrom /mnt
$ cd /mnt
$ ./VBoxLinuxAdditions.run
```



#### 리부팅

우분투를 재부팅 합니다.

