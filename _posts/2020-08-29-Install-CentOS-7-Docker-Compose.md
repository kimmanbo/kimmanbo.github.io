---
title: CentOS 7에 Docker Compose 설치하기
author: Hangyoung Kim
date: 2020-08-29 20:44:00 +0900
categories: [Infrastructure, Docker]
tags: [Docker, docker-compose]
comments: true
pin: false
---

Docker는 설치했다. 이번엔 Docker Compose 설치! ([참고자료](https://docs.docker.com/compose/install/))

### CURL을 통해설치

```shell
# docker compose 설치
sudo curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

# 실행 권한 부여
sudo chmod +x /usr/local/bin/docker-compose
```

※ Alpine 리눅스의 경우, 다음의 패키지 의존성이 존재한다.

```shell
py-pip python-dev libffi-dev openssl-dev gcc libc-dev make
```