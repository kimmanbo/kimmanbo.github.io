---
title: 정규표현식으로 암호 Validation 하기
author: Hangyoung Kim
date: 2021-07-06 12:42:00 +0900
categories: [Web Development, Cheet Sheet]
tags: [Regex]
comments: true
pin: false
---

### 참고자료
- [Stack Overflow](https://stackoverflow.com/questions/19605150/regex-for-password-must-contain-at-least-eight-characters-at-least-one-number-a)


### 정규표현식
- 최소 8자, 문자 >= 1, 숫자 >= 1:
```sh
"^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d]{8,}$"
```
- 최소 8자, 문자 >= 1, 숫자 >= 1, 특수문자 >= 1:
```sh
"^(?=.*[A-Za-z])(?=.*\d)(?=.*[@$!%*#?&])[A-Za-z\d@$!%*#?&]{8,}$"
```
- 최소 8자, 대문자 >= 1, 소문자 >= 1, 숫자 >= 1:
```sh
"^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[a-zA-Z\d]{8,}$"
```
- 최소 8자, 대문자 >= 1, 소문자 >= 1, 숫자 >= 1, 특수문자 >= 1:
```sh
"^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$"
```
- 최소 8자, 최대 10자, 대문자 >= 1, 소문자 >= 1, 숫자 >= 1, 특수문자 >= 1:
```sh
"^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,10}$"
```

