---
title: convex_bottom_bar를 수정해보자
author: Hangyoung Kim
date: 2021-07-08 05:19:00 +0900
categories: [App.Dev., Flutter]
tags: [Flutter]
comments: true
pin: false
---

![Image](https://github.com/hacktons/convex_bottom_bar/raw/master/doc/preview.png)

- [convex_bottom_bar](https://pub.dev/packages/convex_bottom_bar)

### Why modify this great library?

Convex BottomAppBar는 플러터에서 예쁜 하단 네비게이션을 만들어주는 라이브러리다.

간단한 코드로 아래와 같은 예쁜 디자인을 사용할 수 있는데...

![Image](https://github.com/hacktons/convex_bottom_bar/raw/master/doc/appbar-react.gif)

Title을 넣었을 때 하단 여백이 너무 적어서 마음에 안 든다!

코드를 살펴보니 bottom padding이 2로 fix 되어있다.

```dart
      return Container(
        padding: const EdgeInsets.only(bottom: 2),
        child: Column(
          mainAxisAlignment:
              noLabel ? MainAxisAlignment.center : MainAxisAlignment.end,
          children: children,
        ),
      );
    }
```

대충 4 정도로 바꾸면 좋겠다 싶어서 코드를 고치기로 했다.

### How to fix the padding?

별 거 없다.

그냥 git clone 해서 필요한 소스를 프로젝트로 긁어와서 패딩만 수정하면 땡.

스타일 수정에 필요한 코드는 전부 ```lib/src/style``` 안에 들어있다.

### 주의사항

- 혹시 모르니 tag를 확인하고 최신 release로 checkout 한다.
  - 3.0.0 버전에서 Flutter 2.2의 null-safety 수정이 적용되었다.
- Active 된 버튼과 Inactive 상태의 버튼을 따로 return 한다. 둘 다 수정해주자.

### 결과

- 패딩값을 4로 바꾸었더니 딱 내가 원하는 여백이 되었다. (대만족)

- 혹시 싶어서 라이센스를 확인하였는데, Apache 2.0으로 문제 없음!