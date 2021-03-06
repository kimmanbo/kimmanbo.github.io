---
title: NestJS 설치
author: Hangyoung Kim
date: 2021-04-23 20:25:00 +0900
categories: [Node.js, NestJS]
tags: [Node.js, NestJS]
comments: true
pin: false
---

> NestJS에 대해 소개하는 글은 여기저기 많으니까 생략.



※ NodeJS 버전은 12 또는 14를 사용하도록 한다. ([참고](https://github.com/nestjs/nest/issues/4870#issuecomment-638161036))

※ 또한 Yarn을 사용한 설치는 잘 안되는 경우가 있다는 이야기가 있으니, 많이 쓰이는 npm을 사용했다.



### NestJS 설치

```shell
npm i g @nestjs/cli
```

### 프로젝트 생성

```shell
nest new {project-name}
```

이렇게 프로젝트를 생성하면 기본적으로 아래의 파일들이 생성된다.

```
- src
  - app.controller.spec.ts
  - app.controller.ts
  - app.module.ts
  - app.service.ts
  - main.ts
```

NestJS는 제법 타이트한 규칙을 가진 프레임워크다. (마음대로 막 바꾸지 말고 규칙을 따르자!)

\- main.ts 가 NestJS의 시작점이다.

\- \*.spec.ts 파일은 Jest를 활용한 테스트에 사용되는 파일이다.

\- 파일명 규칙도 중요하니 마음대로 바꿔보지 말고 규칙을 찾아서 따르자.

#### 참고자료

- [NestJS Docs](https://docs.nestjs.com/)