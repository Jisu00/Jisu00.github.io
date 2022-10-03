---
title: "[HTML] SVG height 관련 에러 해결"
categories:
  - HTML & CSS
tags:
  - Web
  - CSS
  - Error
date: 2022-10-03
last_modified_at: 2022-10-03
author_profile: true
---

### height 속성에 auto나 current를 주었을 때 발생하는 에러

SVG 태그의 height 속성에 `auto`나 `current`를 주었을 때 아래와 같은 에러가 발생하였다.

> Error: \<svg> attribute height: Expected length, "auto".

### 해결 방법

- height 속성 지우기
- height 속성 값으로 `"100%"` 지정하기
