---
title: "[React] Atomic Design (아토믹 디자인)"
categories:
  - React
tags:
  - Web
  - React
  - Design
date: 2022-10-01
last_modified_at: 2022-10-01
author_profile: true
---

### 유지 보수 및 컴포넌트 재사용 최대화를 위한 디자인 시스템, Atomic Design

<br/>

![image](https://user-images.githubusercontent.com/62230430/193407239-4cdb4368-e6b1-41f9-8914-13c344a00281.png)

Atomic Design은 화학점 관점에서 영감을 얻어 모든 컴포넌트를 Atom(원자)로 구성한 뒤, 이를 바탕으로 상위 컴포넌트들을 만들어 코드의 재사용을 최대화 시킬 수 있는 방법론이다.

아토믹 디자인 이러한 개념을 차용해, Atoms(원자) < 분자(Molecules) < 유기체(Organisms) < 템플릿(Templates) < 페이지(Pages) 5가지 레벨로 나눈다.

### Atom (원자)

- 더 이상 분해할 수 없는 기본 컴포넌트
- 다른 Atom과 결합하여 Molecule 혹은 Organism에서 여러 단위와 결합하여 사용
- 색, 폰트, 애니메이션 같은 추상적인 요소가 포함될 수 있다.

ex ) label, input, button과 같은 기본 HTML 컴포넌트

### Molecule (분자)

- 2개 이상의 원자로 구성되어 있다.

ex ) Input Form, Navigation, Card 등

### Organism (유기체)

- Mocule들을 결합해 유기체 형성

ex ) Form Item을 여러 개 조합한 SignUp Form 등

### Template (템플릿)

- 여러 Organism의 집합
- Page를 만들 수 있도록 컴포넌트를 레이아웃에 배치하고 구조를 잡는 와이어 프레임

### Page (페이지)

- 실제 사용자가 보는 컨텐츠를 담은 화면
- Template에 컴포넌트를 주입

<br/>

#### Reference

- [design systems are for user interfaces](https://bradfrost.com/blog/post/design-systems-are-for-user-interfaces/)
- [아토믹 디자인을 활용한 디자인 시스템 도입기](https://fe-developers.kakaoent.com/2022/220505-how-page-part-use-atomic-design-system/)
- [아토믹 디자인(Atomic Design) 소개 및 실제 사용 경험](https://ghost4551.tistory.com/255)
