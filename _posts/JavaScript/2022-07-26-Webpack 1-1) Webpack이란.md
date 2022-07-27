---
title: "[JS] Webpack) 1-1: Webpack이란?"
categories:
  - JavaScript
date: 2022-07-26
last_modified_at: 2022-07-27
author_profile: true
---

### 하나의 js 파일로 묶어주는 도구, Webpack

<br/>

![webpack](https://user-images.githubusercontent.com/62230430/180939282-5fbb0799-959a-4e9f-8477-6baf53d5357b.png)

**Webpack**이란 여러 개의 리소스 파일(js, css, jpg 등)을 하나의 js로 묶어주는 **모듈 번들러(Module bundler)**이다. 웹팩은 하나의 시작점(Entry point)으로부터 의존적인 모듈을 전부 찾아내 하나의 파일로 만든다.

### 왜 Webpack을 사용해야 할까?

요즘 대부분의 어플리케이션은 React, Vue 혹은 다른 라이브러리들에 의해 만들어진다. 이러한 라이브러리들은 CLI 도구를 제공하는데, 대부분의 환경 설정을 추상화하고 기본 값을 제공한다. 이러한 기본 기능들의 유익함에 대해 이해하려면 기본 값을 조정해볼 필요가 있다.

### 장점

1. 네트워크 접속 부담 감소
2. 서로 다른 패키지들이 같은 이름의 전역 변수를 사용할 때 오작동하는 것을 극복
3. Webpack의 다양한 플러그인을 이용하여 웹 개발시 필요한 다양한 작업 자동화 가능

### 속성

- **Mode** : 모드에 따라 번들링 최적화 진행 (development & production)
- **Entry** : 웹팩에서 웹 자원을 변환하는 데 필요한 진입점 / JS 파일 경로 / 번들링 시작점
- **Output** : 결과물의 파일 경로
- **Module** : 웹팩에서 사용하는 모듈에 대한 설정 / rules를 통해 웹팩 로더 설정
- **Loader** : 웹팩이 다양한 파일 확장자를 다룰 수 있도록 도와주는 서드파티 확장 프로그램들. JS가 아닌 파일들을 모듈로 변경
- **Plugins** : 웹팩의 동작 방식을 바꿔주는 서드파티 확장 프로그램들
- **Target** : 웹팩에서 번들링 결과를 어떤 목표로 하는지 설정 (es5, es2020 등)
- **DevTool** : 소스맵 생성 관련 설정(source-map, inline-source-map 등)


### Reference

- [Opentutorials - Webpack](https://opentutorials.org/module/4566)
- [Webpack을 쓰는 이유](https://ingg.dev/webpack/) 
- [번역) 10분 만에 웹팩 배우기](https://serzhul.io/JavaScript/learn-webpack-in-under-10minutes/)