---
title: CentOS 7에 Docker 설치하기
author: Hangyoung Kim
date: 2020-08-29 20:18:00 +0900
categories: [Infrastructure, Docker]
tags: [Docker]
comments: true
pin: false
---

CentOS 7에서 도커를 설치해보자. ([참고자료](https://docs.docker.com/engine/install/centos/))

### 예전 버전의 Docker 삭제

```shell
sudo yum remove docker \
                docker-client \
                docker-client-latest \
                docker-common \
                docker-latest \
                docker-latest-logrotate \
                docker-logrotate \
                docker-engine
```

### Yum Repository 설정

```shell
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

### Docker Engine 설치

```shell
sudo yum install docker-ce docker-ce-cli containerd.io
```

### (Optional) 버전 지정 설치

```shell
# 설치 가능 버전 확인
yum list docker-ce --showduplicates | sort -r

# 결과 확인
docker-ce.x86_64  3:18.09.1-3.el7                     docker-ce-stable
docker-ce.x86_64  3:18.09.0-3.el7                     docker-ce-stable
docker-ce.x86_64  18.06.1.ce-3.el7                    docker-ce-stable
docker-ce.x86_64  18.06.0.ce-3.el7                    docker-ce-stable
```

```shell
# 버전 지정 설치
sudo yum install docker-ce-<VERSION_STRING> docker-ce-cli-<VERSION_STRING> containerd.io
```

### Docker 시작

```shell
sudo systemctl start docker
```

### Docker 정상동작 확인

```shell
sudo docker run hello-world
```

### (Optional) sudo 없이 docker 실행 설정

```shell
sudo usermod -aG docker $USER
```