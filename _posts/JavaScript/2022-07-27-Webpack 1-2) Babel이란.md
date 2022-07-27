---
title: "[JS] Webpack) 1-2: Babel이란?"
categories:
  - JavaScript
date: 2022-07-27
last_modified_at: 2022-07-27
author_profile: true
---



### 트랜스파일러, Babel

![babel](https://user-images.githubusercontent.com/62230430/181162706-8aad38e7-491a-4a40-b323-423af77951f3.png)

**트랜스파일링(Transpiling)**이란 어떤 특정 언어로 작성된 소스 코드를 다른 소스 코드로 변환하는 것을 말한다.


**Babel**은 JavaScript로 결과물을 만들어주는 컴파일러, 즉 **트랜스파일러(Transpiler)**이다. 

### 왜 굳이 트랜스파일링을?

모든 브라우저에서 새로운 ESNext(ES6+) 문법을 사용할 수 없다 (크로스 브라우징). 따라서 Babel과 같은 트랜스파일러를 통해 **구형 브라우저에서도 동작할 수 있는 ES5 이하의 코드로 변환** 시켜주는 것이 필수적이다.


### Reference

- [Transpile, 트랜스파일링(Transpiling)](https://velog.io/@dahye-program/Transpile-Transpile-%ED%8A%B8%EB%9E%9C%EC%8A%A4%ED%8C%8C%EC%9D%BC%EB%A7%81Transpiling)