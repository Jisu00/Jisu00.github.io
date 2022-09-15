---
title: "[Axios] Interceptors"
categories:
  - Axios
tags:
  - Web
  - Axios
date: 2022-09-15
last_modified_at: 2022-09-15
author_profile: true
---

### axios 요청 및 응답 전에 작업 수행

> [Axios 공식 문서 - 인터셉터](https://axios-http.com/kr/docs/interceptors)

인턴 회사에서 제작하고 있는 서비스의 access token의 유효 기간인 2시간이 지날 경우, 무조건 로그아웃 되어버리는 이슈가 존재했다. 이를 해결하기 위해 refresh token을 도입하게 되었고, 각 token들의 유효 기간 만료 여부를 **요청 이전에 확인하는 과정이 필요**했다.

**axios의 interceptors**를 사용하면 `then` 또는 `catch`로 처리되기 전에 요청과 응답을 가로챌 수 있다.

### 요청 인터셉터

```js
axios.interceptors.request.use(
  function () {
    // 요청 전달 전에 수행될 작업
    return config;
  },
  function (err) {
    // 요청 오류가 있을 때 수행될 작업
    return Promise.reject(err);
  }
);
```

### 응답 인터셉터

```js
axios.interceptors.response.use(
  function (res) {
    // 2xx 상태 코드일 때 트리거, 응답 데이터가 있는 작업 수행
    return res;
  },
  function (err) {
    // 2xx 이외의 상태 코드일 때 트리거, 응답 오류가 있는 작업 수행
    return Promise.reject(err);
  }
);
```
