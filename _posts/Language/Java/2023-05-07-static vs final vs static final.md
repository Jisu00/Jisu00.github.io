---
title: "[Java] static vs final vs static final"
categories:
  - Java
tags:
  - Java
date: 2023-05-07
last_modified_at: 2023-05-07
author_profile: true
---

### 고정된? 최종의? 고정된 최종의?

static과 final, 그리고 static final의 개념에 대해 알아보자.


### static

```java
public class Sample {
  static int number;

  static int add(int x, int y) { return x + y; }
}
```


- 객체 생성 없이 사용할 수 있는 필드 또는 메소드를 생성하고자 할 때 활용
- 동일한 클래스의 모든 객체들에 의해 공유 => 공용 데이터에 해당할 때 이용
- `Sample.add()`, `Sample.number`처럼 바로 사용 가능
- `this` 키워드 사용 불가능


### final

```java
public class Shop {
  final int closeTime = 21; // 방법 1) 선언과 동시에 값 지정
  final int openTime;

  public Shop(int openTime) {
    this.openTime = openTime; // 방법 2) 생성자를 통한 값 지정
  }
}
```

- 수정 불가능한 최종적인 변수
- 선언과 동시에 값을 지정하는 방법과 생성자를 통해 값을 지정하는 방법 존재
  - 생성자를 통해 지정할 경우, 객체마다 다르게 설정 가능


#### static final

```java
static final double PI = 3.14;
```

- 모든 영역에서 고정된 값으로 사용하는 상수
  - `final`과의 차이점

<br/>

#### Reference

- [[Java] static, final, static final의 차이](https://gobae.tistory.com/3)