---
title: Docker Compose로 MariaDB 실행하기
author: Hangyoung Kim
date: 2020-08-29 23:14:00 +0900
categories: [Infrastructure, Docker]
tags: [Docker, docker-compose, MariaDB]
comments: true
pin: false
---

Docker-Compose를 사용하여 MariaDB 컨테이너 띄우기.

### docker-compose.yml

```
version: '3.7'

services:
  mariadb:
    container_name: docker-mariadb
    image: mariadb:10.5.5
    init: true
    user: root
    restart: always
    command:
      - --default-authentication-plugin=mysql_native_password
      - --character-set-server=utf8mb4
      - --collation-server=utf8mb4_unicode_ci
    volumes:
      - ${SOME_DIRECTORY}/mariadb/data:/var/lib/mysql
      - ${SOME_DIRECTORY}/mariadb/config:/etc/mysql/conf.d
    ports:
      - 3306:3306
    env_file: .env
    environment:
      TZ: Asia/Seoul
```

\- version:

docker-compose file format version으로 변화가 제법 많은 편인 듯 하다.

여기서는 init 옵션을 주기 위해 3.7을 사용했다. (3.7에 추가된 옵션)

\- init:

컨테이너의 프로세스 감지/관리 방식을 바꿔서 좀비 프로세스 발생을 막아주는 듯... 한데 좀 더 찾아봐야함.

### .env

```
MYSQL_HOST=127.0.0.1
MYSQL_PORT=3306
MYSQL_ROOT_PASSWORD= { Root 암호 }
MYSQL_DATABASE= { 초기 데이터베이스명 }
MYSQL_USER= { 초기 유저 계정 }
MYSQL_PASSWORD= { 초기 유저 암호 }
```

### (Optional) Database 초기 생성시 sql문을 실행시키고 싶다면?

```
${SOME_DIRECTORY}/mariadb/init:/docker-entrypoint-initdb.d
```

volumes에 위와 같은 코드를 추가하고, init 디렉토리에 sql 파일들을 넣어두면 된다.

참고로 sql 파일들은 알파벳 순서로 실행되므로 insert를 create 전에 호출하는 등의 일이 발생하지 않도록 주의.

또한 data 디렉토리에 데이터가 존재하면 수행되지 않았던 것으로 기억...

### 실행

```
$ docker-compose up -d
```
