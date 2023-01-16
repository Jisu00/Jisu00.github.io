---
title: "[FE] Cookie vs Session vs Token"
categories:
  - Front-end
tags:
  - Web
  - FE Knowledge
  - Authentication
date: 2023-01-16
last_modified_at: 2023-01-16
author_profile: true
---

### 헷갈리는 Cookie, Session, Token, JWT의 개념과 특징 짚고 넘어가기

<br/>

#### Cookie

**특징**

- 서버는 Cookie를 이용하여 사용자의 브라우저에 data를 넣을 수 있음.
- Cookie 저장 이후, 해당 웹사이트를 방문할 때마다 해당 Cookie도 함께 요청보내게 됨.
- 도메인에 따라 제한
- 유효기간 존재 (서버가 정한 기간)
- 인증뿐 아니라 여러 정보 저장 가능
- 웹에만 존재, App에는 없음.
- 공간 제약 존재

#### Session

HTTP 프로토콜은 stateless이기 때문에 메모리가 없어 요청끼리의 연결이 존재하지 않는다. 따라서 요청할 때마다 사용자를 판별해주어야 한다.

**인증 예시**

> 1. 브라우저에서 사용자명과 비밀번호를 서버에 전송
> 2. 비밀번호가 맞으면 서버는 Session DB에 유저 생성
> 3. (Session에는 unique한 id가 존재) Session id가 Cookie를 통해 브라우저로 돌아오고 저장됨.
> 4. 같은 웹사이트의 다른 페이지로 이동하면 Session id를 가지고 있는 Cookie를 서버에 전송
> 5. (Cookie는 자동 전송) 서버로 들어오는 Cookie와 Session id를 확인
> 6. Session id를 가지고 Session DB 확인하여 해당 사용자명을 알게 됨. (이 때 서버는 사용자가 누군지 인식)

**특징**

- 중요한 유저 정보는 모두 서버에 있고, 유저는 Session id만 가지고 있음.
- 현재 로그인한 유저들의 모든 Session id를 DB에 저장해야 함.
  - 이로 인한 추가 기능 구현 가능 (ex. 특정 유저 탈퇴, 원하지 않는 디바이스 강제 로그아웃)
  - DB를 구매하고 유지해야 함.
- 매요청마다 전송 및 인증 필요
- Cookie는 Session id를 전달하기 위한 매개체로만 사용

#### Token

iOS, Android 앱을 만들 때 네이티브 앱에는 Cookie가 없기 때문에, 이러한 경우에 Token을 사용한다.

**특징**

- String 형식
- Token을 서버에 보내고, 서버는 Session DB에서 해당 Token과 일치하는 유저를 찾음.
- 매요청마다 전송 및 인증 필요

#### JWT

**인증 예시**

> 1. 브라우저에서 사용자명과 비밀번호를 서버에 전송
> 2. 서버는 사용자명을 통해 **Signature**을 사용하여 서명
> 3. String 형태의 Token으로 브라우저에 전송
> 4. 서버에 요청 보낼 때, Sign된 Token를 전송
> 5. 서버는 해당 Token의 Signature이 유효한지 확인
> 6. Token이 유효하면 인증 완료

**특징**

- Token 형식
- 사용자를 인증하는데 필요한 정보를 Token에 저장
- Session DB 사용 불필요
- 공간 제약 X
- 암호화 X, 중요한 정보를 포함시키면 안 됨.
- 생성된 Token을 추적하지 않고 유효한지의 여부만 확인
  - DB 생성할 필요 X
  - Session에서 구현할 수 있는 사용자에 관한 기능 구현 불가능

<br/>

#### Reference

- [세션 vs 토큰 vs 쿠키? 기초개념 잡아드림. 10분 순삭!](https://www.youtube.com/watch?v=tosLBcAX1vk)
