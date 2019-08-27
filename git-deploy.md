# git deploy

git init --bare


cd hooks
vi post-receive

```sh
#!/bin/bash
git --work-tree=/var/www/html --git-dir=/home/nugupoem/bare.git checkout -f

```

실행파일 추가
```bash
chmod +x post-receive
```

## 개발PC

git remote add server ssh://root@101.101.164.248/home/nugupoem/bare.git
